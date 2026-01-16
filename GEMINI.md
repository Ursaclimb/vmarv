# Project Overview

This repository is an Umbrel Community App Store. It contains a collection of community-maintained apps for Umbrel servers. The main configuration file `umbrel-app-store.yml` defines the store's ID as `notrin` and its name as "NotRin7's App Store".

The repository is structured with each application residing in its own directory, prefixed with `notrin-`. Each application directory contains the necessary files to define and run the app on an Umbrel instance.

## Application Structure

Each application within this app store follows a consistent structure:

*   `umbrel-app.yml`: This manifest file contains metadata about the application, such as its ID, name, category, version, description, and more. It is used by the Umbrel UI to display information about the app.
*   `docker-compose.yml`: This file defines the Docker services required to run the application. It specifies the Docker images, volumes, and environment variables needed for the app to function correctly.

Some applications may have additional files and directories, such as:

*   `exports.sh`: A script to export data from the application.
*   `api/`: A directory containing a custom API for the application.
*   `gui/`: A directory containing a custom user interface for the application.
*   `hooks/`: A directory for scripts that are executed at different stages of the app's lifecycle.

## Building and Running

The applications in this repository are not built or run directly from the command line. Instead, they are intended to be installed and managed through the Umbrel user interface.

To use these applications, you need to add this repository as a community app store to your Umbrel server.

1.  Navigate to the **App Store** section in your Umbrel dashboard.
2.  Click the "..." menu in the top right corner and select **Community App Stores**.
3.  Paste the following URL into the field and click **Add**:

    ```
    https://github.com/NotRin7/umbrel-community-app-store
    ```

4.  The apps from this store will then be available for installation in your Umbrel App Store.

## Development Conventions

The repository follows the conventions expected by the Umbrel operating system for community app stores. Each app is self-contained within its own directory and provides the necessary `umbrel-app.yml` and `docker-compose.yml` files.

When adding a new app, the directory name should be prefixed with `notrin-` and it should contain at least the two aforementioned YAML files.
