# Build tools task

## Part 1: Webpack

Write a configuration within the `ui/webpack.config.js` file to *build* a frontend application:
* Specify the entry point of the application as `ui/src/index.js`.
* Set the output filename for the built application to be `app.js`.
* Define the output destination as the directory `ui/dist`.
* Utilize the [HtmlWebpackPlugin](https://webpack.js.org/plugins/html-webpack-plugin/) to copy `ui/src/index.html` to the `ui/dist` directory, ensuring that the HTML file is included in the build output.
* Use [CopyWebpackPlugin](https://webpack.js.org/plugins/copy-webpack-plugin/) to copy `ui/src/style.css` to the `ui/dist/css` directory, maintaining the specified subfolder for organization.

To build the application with `Webpack`, execute the following commands from your terminal:

```bash
cd ui
npm i
npm run build
```


## Part 2: Gradle

**Requirements**: Ensure that `Java Development Kit (JDK) 17` is installed before executing the `Gradle` build.

Within your `build.gradle.kts`, configure the Gradle build system to seamlessly integrate with the `Webpack` setup you've previously defined:
* Define a task named `npmInstall` of type `Exec` that will set the working directory to ui and run the command `npm i`.
* Define a task named `compileUi` of type `Exec`, setting the working directory to `ui`, and execute `npm run build`. Ensure this task is dependent on the `npmInstall` task.
* Create a task named `copyUi` of type `Copy` that copies `ui/dist/index.html`, `ui/dist/app.js` file and `ui/dist/css` folder into `src/main/resources` directory. This task should depend on the `compileUi` task.
* Ensure that all tasks of type `org.springframework.boot.gradle.tasks.run.BootRun` depend on the `opyUi` task before executing.

To run the entire build process and serve the application, use the following command in your terminal:

```bash
./gradlew bootRun
```

You can then view your application, showcasing a delightful list of dogs, at [http://localhost:8080](http://localhost:8080).

Store all written configurations, including the `Webpack` configuration and `Gradle` setup, in this `GitHub` repository.
