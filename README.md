# Maven-Project
# Simple Java Maven Application

## Description

This is a simple Java application that prints "Hello, World!" to the console.  
It is structured as a Maven project.

## Build & Run

1. **Build the project**
    ```sh
    mvn clean package
    ```

2. **Run the application**
    ```sh
    java -cp target/simple-java-maven-app-1.0-SNAPSHOT.jar com.example.App
    ```
# How to Run a Maven Java Project in Jenkins

## Prerequisites
- Jenkins is installed and running.
- You have the required permissions to configure jobs.
- The Maven plugin is installed in Jenkins.
- Java and Maven are installed on the Jenkins server or agents.

## Steps

1. **Create a New Jenkins Job**
   - Go to your Jenkins dashboard.
   - Click on **"New Item"**.
   - Enter a name (e.g., `simple-java-maven-app`).
   - Select **"Freestyle project"** and click **"OK"**.

2. **Configure Source Code Management**
   - Under **"Source Code Management"**, select **"Git"**.
   - Enter your repository URL (e.g., `https://github.com/your-user/simple-java-maven-app.git`).
   - Add credentials if your repo is private.

3. **Add Build Step**
   - Scroll down to **"Build"**.
   - Click **"Add build step"** and choose **"Invoke top-level Maven targets"**.
   - In the **"Goals"** field, enter:
     ```
     clean package
     ```
   - (Optional) If you need to specify a particular `pom.xml`, use the "POM" field.

4. **(Optional) Add Post-build Actions**
   - For example, you can archive the built `.jar` by adding "Archive the artifacts" and entering:
     ```
     target/*.jar
     ```

5. **Save and Build**
   - Click **"Save"**.
   - On the job page, click **"Build Now"**.
   - Check the **"Console Output"** to see the progress and verify the build.

## Running the Application

- By default, Jenkins will only build the project. If you want Jenkins to actually run your Java application after building:
  - Add another build step: **"Execute shell"** (Linux/macOS) or **"Execute Windows batch command"**.
  - Enter:
    ```sh
    java -cp target/simple-java-maven-app-1.0-SNAPSHOT.jar com.example.App
    ```
  - This will execute your main class after building.

---

**Tip:** For more automation, consider using a Jenkinsfile and Pipeline jobs for advanced workflows.
