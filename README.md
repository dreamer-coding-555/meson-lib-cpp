# Project Template README

Welcome to the **Project Template** repository! This README provides user-friendly instructions for setting up, compiling, testing, and running a project using the Meson build system on Windows, macOS, and Linux systems. Please note that the Meson build system is required for successfully building this project.

## Who is This For?

This guide is designed for developers of all skill levels who want to use the Meson build system for their projects. It assumes basic familiarity with command-line interfaces and project organization.

## Prerequisites

Before getting started, make sure you have the following installed:

- **Meson Build System**: This project relies on Meson. If you don't have Meson installed, visit the official [Meson website](https://mesonbuild.com/Getting-meson.html) for installation instructions.

## Setting up Meson Build

1. **Install Meson**:
   - Follow the installation instructions on the [Meson website](https://mesonbuild.com/Getting-meson.html) for your operating system.

## Setting up, Compiling, Installing, and Running the Project

1. **Create a Wrap File**:

Create a directory named subprojects in the root directory, next create a file named `tscl-x<name>-cpp.wrap` in the `subprojects` directory of your project with the following content:

   ```bash
   # ================ #
   #  FSCL Wrap File. #
   # ================ #
   [wrap-git]
   url = https://github.com/fossil-lib/fscl-<name>-cpp.git
   revision = main
   
   [provide]
   fscl-x<name>-cpp = fscl_x<name>_cpp_dep
   ```

2. **Integrate Wrap File in Meson Build**:
   ```meson
   project('my_project', 'c',
       version : '0.1',
       default_options : ['warning_level=3'])

   exe = executable('my_project', 'my_project.cpp',
       dependencies : dependency('fscl-x<name>-cpp'), # add this line
       install : true)

   test('basic', exe)
   ```

3. **Compile the Project**:
   ```bash
   meson setup builddir
   meson compile -C builddir
   ```

## Including the Demo and Running Tests

To run tests, you can use the following options when configuring the build:

- **Running Tests**: Add `-Dwith_test=enabled` when configuring the build.

Example:

```bash
meson setup builddir -Dwith_test=enabled
```

## Contributing

If you're interested in contributing to this project, please consider opening pull requests or creating issues on the [GitHub repository](https://github.com/dreamer-coding-555/meson-lib-cpp).

## Feedback and Support

If you encounter any issues, have questions, or would like to provide feedback, don't hesitate to open an issue on the [GitHub repository](https://github.com/dreamer-coding-555/meson-lib-cpp/issues).

## License

This project is licensed under the [Mozilla Public License](LICENSE).

---

Thank you for choosing this project with the Meson build system. Happy coding and building amazing projects!
