# Step by Step Guide to Gulp JS
Resources: <br>
[Gulp](https://gulpjs.com/) <br>
[Gulp Guide](https://gulpjs.com/docs/en/getting-started/quick-start/) <br>
<br>
## - Step 1
### Install Node.js and npm
<br>

1. *Download Node.js:*  

    - Download the LTS (Long Term Support) version suitable for your operating system <br>
2. *Install Node.js:*  

    * Run the installer you downloaded  
    * Follow the prompts to complete the installation
    * The installer will also install npm automatically <br>
3. *Verify Installation:*
    - Open your terminal (Command Prompt on Windows, Terminal on macOS/Linux)
    - Type **`node -v`** and press Enter. You should see the version number of Node.js
    - Type **`npm -v`** and press Enter. You should see the version number of npm
<br>      

## Step 2
### Set Up A New Project
<br>

1. *Create a Project Directory:*
     - Open your terminal
     - Navigate to the directory where you want to create your project
     - Create a new directory for your project: **`mkdir my-gulp-project`**
     - Navigate into the directory: **`cd my-gulp-project`**

2. *Initialise npm*
    - In your project directory, initialize a new npm project: **`npm init -y`**
    - This creates a **`package.json`** file with default settings
<br>      

## Step 3
### Install Gulp
<br>

1. *Install Gulp Globally:*
     - This allows you to use the Gulp command line tool: **`npm install --global gulp-cli`**
       

2. *Install Gulp Locally:*
    - Install Gulp in your project directory: **`npm install --save-dev gulp`**
<br>      

## Step 4
### Create A Gulp File
<br>

1. *Create a **`gulpfile.js`**:*
     - In your project directory, create a new file named **`gulpfile.js`**
     - This file will contain the tasks Gulp will perform
<br>      

## Step 5
### Write Your First Gulp Task
<br>

1. *Open **`gulpfile.js`**:*
     - Open the file in a text editor of your choice

2. *Require Gulp:*
    - Add the following line at the top of the file to import Gulp:
```const gulp = require('gulp');```

3. *Create a Default Task:*
    - Add a simple task to test your setup:
```
gulp.task('default', (done) => {
    console.log('Gulp is running!');
    done();
});
```
<br>      

## Step 6
### Run Gulp
<br>

1. *Run The Default Task:*
    - In your terminal, make sure you're in your project directory
    - Type **`gulp`** and press Enter
    - You should see the message "Gulp is running!" in your terminal
<br>      

## Step 7
### Create More Gulp Tasks
<br>

1. *Copy Files:*
     - Add a task to copy files from one directory to another:
```
const gulp = require('gulp');

gulp.task('copy-html', () => {
    return gulp.src('src/*.html')
        .pipe(gulp.dest('dist'));
});

gulp.task('default', gulp.series('copy-html'));
```

2. *Run the New Task:*
     - Create a directory named `src` in your project directory
     - Add an HTML file in the `src` directory
     - Run `gulp` in your terminal
     - Check the `dist` directory to see if the HTML file has been copied

<br>      

## Step 8
### Automate Tasks with Watch
<br>

1. *Add a Watch Task:*
     - Update `gulpfile.js` to watch for changes and automatically run tasks:
```
const gulp = require('gulp');

gulp.task('copy-html', () => {
    return gulp.src('src/*.html')
        .pipe(gulp.dest('dist'));
});

gulp.task('watch', () => {
    gulp.watch('src/*.html', gulp.series('copy-html'));
});

gulp.task('default', gulp.series('copy-html', 'watch'));
```

2. *Run the Watch Task:*
     - Run `gulp` in your terminal
     - Modify the HTML file in the `src` directory and save it
     - The changes should be automatically copied to the `dist` directory
<br>      

## Step 9
### Using Plugins
<br>

1. *Install a Plugin:*
     - For example, to use the `gulp-uglify` plugin to minify JavaScript files: `npm install --save-dev gulp-uglify`

2. *Use The Plugin:*
    - Update `gulpfile.js` to minify JavaScript files:
```
const gulp = require('gulp');
const uglify = require('gulp-uglify');

gulp.task('minify-js', () => {
    return gulp.src('src/*.js')
        .pipe(uglify())
        .pipe(gulp.dest('dist'));
});

gulp.task('watch', () => {
    gulp.watch('src/*.js', gulp.series('minify-js'));
});

gulp.task('default', gulp.series('minify-js', 'watch'));
```

3. *Run The Task:*
    - Add a JavaScript file in the **`src`** directory.
    - Run **`gulp`** in your terminal.
    - Check the **`dist`** directory to see the minified JavaScript file.


