---
title: Room Database
parent: 3rd party Intergrations
layout: home
nav_order: 5
---

## Saving data locally with Room ##

Room is a library that provides an abstration layer over SQLite. SQLite 
is an embedded,file-based RDBMS ie. it doesn't not require a server to run it, making
it ideal to run on Android devices. SQL is supported in SQlite, alot if not all relational
database topics translate over to SQLite.

There are 3 requirements when integrating SQLite into your projects:
1. Room Database - the SQLite database
2. Data Access Object (DAO) - Interface typically filled with CRUD operations. The DAO interacts with the database.
3. Entities - Business tier of application ie. the data is contained within entities that have a 1 to 1 relationship 
with tables in the database. 

See below for a visual of the same.

![Room Architecture](img/room_architecture.png)

### Setting up Room in your application ###

1. Add library dependecies to project.

libs.versions.toml file
```kotlin
[versions]
roomRuntime = "2.6.1"
ksp="1.9.0-1.0.13"
roomCommon = "2.6.1"

[libraries]
androidx-room-ktx = { module = "androidx.room:room-ktx", version.ref = "roomRuntime" }
androidx-room-room-compiler = { module = "androidx.room:room-compiler", version.ref = "roomRuntime" }
androidx-room-runtime = { module = "androidx.room:room-runtime", version.ref = "roomRuntime" }
androidx-room-common = { group = "androidx.room", name = "room-common", version.ref = "roomCommon" }

[plugins]
devtoolsKsp = { id = "com.google.devtools.ksp", version.ref = "ksp"}
```

build.gradle.kts (module :app)

```kotlin
plugins{
    alias(libs.plugins.devtoolsKsp)
}

dependencies{
    // room
    implementation(libs.androidx.room.runtime)
    implementation(libs.androidx.room.ktx)
    implementation(libs.androidx.room.common)
    annotationProcessor(libs.androidx.room.room.compiler)
    ksp(libs.androidx.room.room.compiler)
}
```
**Please remember to sync files after making changes** This will download and install 
room library. KSP is a Kotlin-specific tool designed for annotation processing, developed 
by JetBrains and Google. It allows you to read and analyze Kotlin code and generate source files during the build process.

2. Create an abstract class that inherits from RoomDatabase and setup
a singleton instance to retreive the database application. A singleton
is a design pattern that ensure that 1 instance of an object exists in 
an application.

```kotlin
@Database(entities = [Movie::class], version = 2, exportSchema = false)
@TypeConverters(Converters::class)
abstract class AppDatabase : RoomDatabase() {
    abstract fun movieDao(): MovieDao

    // companion object implements Singleton Pattern
    companion object{
        @Volatile
        private var INSTANCE: AppDatabase? = null

        fun getInstance(context: Context): AppDatabase{
            return INSTANCE ?: synchronized(this){
                val instance = Room.databaseBuilder(
                    context.applicationContext,
                    AppDatabase::class.java,
                    "MovieHub Project 2024"
                )
                    .fallbackToDestructiveMigration() // no need to worry managing migrations, odd still have to update version info from 1 to 2
                    .build()
                INSTANCE = instance
                instance
            }
        }
    }

}
```

**A few things to note.** Annotations are sprinkled throughout the code. An annotation is 
prefixed with the `@` symbol and therefore easy to spot in code. `@Database` `@TypeConverters` and `@Votile1`
are all examples of annotations. When KSP reads an annotation is generates code behind the scenes. 
For example the `@Database` annotation might generate code like the following:
```sql
    CREATE DATABSASE MovieHub Project 2024
```

3. Create a Interface Data Access Object (DAO)

```kotlin
@Dao
interface MovieDao {
    @Insert(onConflict = OnConflictStrategy.REPLACE)
    fun insertAllMovies(movies: List<Movie>)

    @Query("SELECT * FROM movies WHERE id = :id")
    fun getMovieById(id: Int): Movie?

    @Update
    fun updateMovie(movie: Movie)


}
```

Please note annoations are used here aswell. `@Dao` `@Insert` `@Query` `@Update`
are all examples of this.

4. Create a instance of the database instance.

```kotlin
    // get db instance
    val db = AppDatabase.getInstance(applicationContext)
```

Now the database can be used within the application.

A **common practice**  is to perform database operations in a 
seperate thread (aka co-routine) this prevents the application
from being unresponsive when operations take longer than a few seconds. 
Use cases for this include pulling data from an API or performing buld
operations on a database. Think of how frustrated users of your applicatoin would be 
if they had to wait 30 seconds to interact with the app. 

```kotlin
 GlobalScope.launch {
    saveDataToDatabase(database = database, _moviesResponse.value)
}
private suspend fun saveDataToDatabase(database: AppDatabase, movies: List<Movie>){
    database.movieDao().insertAllMovies(movies)
}
```

