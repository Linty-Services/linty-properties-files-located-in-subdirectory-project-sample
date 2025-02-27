# Analyzing project with property files located in linty-conf subdirectory

Let's assume that scans are run from the root of the repository.

## `sonar-project.properties`

The file is not located at the root of the repository but in the `linty-conf` subdirectory, and it has been renamed to
`linty-project.properties`.

To tell Linty where to find this file, add `-Dproject.settings=./linty-conf/linty-project.properties` to the scanner.
See [.github/workflows/linty.yml](.github/workflows/linty.yml).

All paths in this file remain relative to where the scan is run from (from the root of the repository in this example).

## BugFinder configuration files

The `read.ys` and `hierarchy.ys` files are not located at the root of the repository but in the `linty-conf`
subdirectory.

To tell Linty where to find these files, navigate to your project on the Linty web interface, then go to **Project
Settings > General Settings > HDL** and set the following properties:

* `sonar.bugfinder.readScriptPath` to `./linty-conf/read.ys`
* `sonar.bugfinder.hierarchyScriptPath` to `./linty-conf/hierarchy.ys`

Paths for these properties are relative to where the scan is run from (from the root of the repository in this example).

Paths in these files are relative to these files' locations. For instance, path of `sleep.vhd` is `../src/sleep.vhd`
relative to `linty-conf/read.ys`.
