# Command line interface
## Basic usage

To run cellfinder, use this general syntax

```bash
    cellfinder -s signal_channel_images  optional_signal_channel_images -b background_channel_images -o /path/to/output_directory -v 5 2 2 --orientation asl
```

:::{hint}
All options can be found by running `cellfinder -h`
:::

## Arguments

### Mandatory

* `-s` or `--signal-planes-paths` Path to the directory of the signal files. Can also be a text file pointing to the 
files. **There can be as many signal channels as you like, and each will be treated independently**.
* `-b` or `--background-planes-path` Path to the directory of the background files. Can also be a text file pointing to 
the files.  **This background channel will be used for all signal channels**
* `-o` or `--output-dir` Output directory for all intermediate and final results

:::{caution}
You must also specify the orientation and voxel size of your data, see 
[Image definition](/documentation/general/image-definition).
:::

### The following options can also be used:

**Only run parts of cellfinder**

If for some reason you don't want some parts of cellfinder to run, you can use the following options. 
If a part of the pipeline is required by another part it will be run (i.e. `--no-detection` won't do 
anything unless `--no-classification` is also used). cellfinder will attempt to work out what parts of the 
pipeline have already been run (in a given output directory) and not run them again if appropriate.

* `--no-register` Do not run registration&#x20;
* `--no-detection` Do not run cell candidate detection
* `--no-classification` Do not run cell classification
* `--no-analyse` Do not analyse and export cell positions
* `--no-figures` Do not create figures (e.g. heatmap)

**Figures options**

Figures cannot yet be customised much, but the current options are here:

* `--heatmap-smoothing` Gaussian smoothing sigma, in um.
* `--no-mask-figs` Don't mask the figures (removing any areas outside the brain, from e.g. smoothing)

**Performance, debugging and testing**

* `--debug` Increase verbosity of statements printed to console and save all intermediate files.
* `--n-free-cpus` The number of CPU cores on the machine to leave unused by the program to spare resources.
* `--max-ram` Maximum amount of RAM to use (in GB) — **not currently fully implemented for all parts of cellfinder**

Useful for testing or if you know your cells are only in a specific region

* `--start-plane` The first plane to process in the Z dimension
* `--end-plane` The last plane to process in the Z dimension

**Standard space options**

* `--transform-all` Transform all cell positions (including artifacts).

## Additional options
```{toctree}
:maxdepth: 1
candidate-detection
classification
/documentation/brainreg/user-guide/parameters
```

:::{hint}
If you're using cellfinder at the [Sainsbury Wellcome Centre](https://www.sainsburywellcome.org/web/),
you may wish to see the [instructions for using cellfinder on the SWC HPC system](using-cellfinder-at-the-swc).
:::

```{toctree}
:maxdepth: 1
:hidden:
using-cellfinder-at-the-swc
```
