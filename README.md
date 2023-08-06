# ur5e_mj_description

UR5e model files for [mc_mujoco](https://github.com/rohanpsingh/mc_mujoco).

## Install

```bash
mkdir build
cd build
cmake ..
make && sudo make install
```

## CMake options

- `SRC_MODE` if `ON` the files loaded by mujoco will point to the source rather than the installed files (default `OFF`)

## License
XML and asset files in [the xml directory](https://github.com/mmurooka/ur5e_mj_description/tree/master/xml) of this repository are subject to a different license term. Please consult the LICENSE file under the xml directory for the relevant license and copyright information.
