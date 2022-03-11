
## Testing and Database in Shiny

### Brief description

Testing is essential to all the applications and code that we develop, including Shiny app. There are few different testing strategies we can apply to cover all layers of the Shiny architecture, such as the backend functionality, client-server interactions as well as interactions with the web browsers. Shiny provides a package `shinytest` that simulates the app for our automating testing.

### Long description

<br>

**Packages and technologies used for testing the app**

Broadly speaking, there are three categories of automated tests that we can design for Shiny with respective packages.

- Unit test: These are the test cases that is designed against the non-reactive functions. For example, retrieving data from a database, or data processing. By using the [`testthat`](http://testthat.r-lib.org/) package, we can verify the behaviour of the code that are extracted out of the server function or UI, similar to the test cases that we write for a new package development. To start, we can make use of the command `usethis::use_test()` that creates test files and all other infrastructures needed.

- Server function tests: These are the test cases that run to simulate a client session. For example, we mimic a user input through R commands and check against the expected results and server output. To achieve, the function [`testServer()`](https://shiny.rstudio.com/articles/server-function-testing.html) can be used, that we specify input and record the server output. Then by combining `testthat` we can automate the checking of the actual output and expected output.

- Snapshot-based tests: Since Shiny 1.5.0, it introduces the snapshot-based test by a new function `recordTest()`. This is the test that allows user to capture the interactions from a web browser along with screenshots. It is useful for testing the full user experience. However, since it records the interactions from a web browser, the script recorded are very senstiive to any user interface changes and requires frequent script maintenance to that.

There are other kinds of testing that can be considered based on user requirements. For example, if the app requires a quick response time of displaying a chart, or requires to support a large amount of concurrent users, load testing against the hardware environment of the application would be needed.

**Storage and Database**

Shiny supports both local and remote connection to storge and database. By default, Shiny supports to save and load data files such as CSV to the local server. It is also a common practice to store the data in a server other than the Shiny app server. In order to use other storages, respective R packages should be installed. The following are an overview of the storage support and the R package required.

| Method            | Local storage | Remote storage | R package     |
|-------------------|:-------------:|:--------------:|---------------|
| Local file system |      YES      |                | -             |
| Dropbox           |               |       YES      | rdrop2        |
| Amazon S3         |               |       YES      | aws.s3        |
| SQLite            |      YES      |                | RSQLite       |
| MySQL             |      YES      |       YES      | RMySQL        |
| Google Sheets     |               |       YES      | googlesheets4 |
| MongoDB           |      YES      |       YES      | mongolite     |

### Links

- [Shiny testing overview](https://shiny.rstudio.com/articles/testing-overview.html)
- [Mastering Shiny](https://mastering-shiny.org/scaling-testing.html)
- [testthat package](http://testthat.r-lib.org/)
- [testServer function](https://shiny.rstudio.com/articles/server-function-testing.html)
- [Persistent data storage in Shiny apps](https://shiny.rstudio.com/articles/persistent-data-storage.html#local-vs-remote)
