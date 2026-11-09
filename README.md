# ECE 5775 — Car/Truck CNN Accelerator

HLS CNN inference coursework for car/truck classification on the ZedBoard. `ecelinux/` contains HLS kernels, learned parameters, test inputs, and C simulation; `zedboard/` contains the host-oriented variant. Model weights and test fixtures are retained because simulation reads them.

Requires the matching Vivado HLS headers/libraries and a C++11 compiler. After sourcing your Vivado HLS environment:

```sh
cd ecelinux
make csim
# Historical HLS entry point, after repairing its input-data reference:
# vivado_hls -f run_more.tcl
```

The historical Tcl scripts refer to a `data` input directory that is absent in this snapshot; available inputs are `data2/` and `test_data2/`. The bitstream scripts also expect external ZedBoard/Xillybus project support. Therefore full HLS/board regeneration requires restoring those dependencies. `make bitstream` and `make vivado` reference a missing `run.tcl`; use the existing named scripts only after reviewing them. Avoid historical `make clean` targets before backing up source fixtures. No synthesis, accuracy, or hardware result is newly asserted here. The [U55C port](https://github.com/matthales123/u55c-car-truck-cnn) is a separate later project.

The saved `zedboard/data2` and `zedboard/test_data2` entries are text placeholders containing relative paths, not working directories. Restore their links to the corresponding `ecelinux/` inputs before using that host variant.

Source comments retain course, instructor, library, and collaborator attribution. This repository does not grant a new license over third-party material. Generated logs, waveforms, debugging captures, and result directories are omitted from this public source edition.
