# Visualising brainreg output
If you have used the brainreg command-line interface, or simply want to view results at a later time, 
brainreg comes with a plugin for napari to allow you to easily view registration results.

## Usage
Typically, you would view the results in sample space, i.e. with registration results overlaid on your data.

To begin, open napari and drag your brainreg output directory (the one with the log file) onto the napari window.

Various images should then open, including:

* `Registered image` - the image used for registration, downsampled to atlas resolution
* `atlas_name` - e.g. `allen_mouse_25um` the atlas labels, warped to your sample brain
* `Boundaries` - the boundaries of the atlas regions

If you downsampled additional channels, these will also be loaded.

Some of these images will not be visible by default. Click the little eye icon to toggle visibility.

:::{note}
N.B. If you use a high-resolution atlas (such as `allen_mouse_10um`), then the files can take a little while to load.
:::

![Visualisation in sample space](/documentation/brainreg/images/sample_space.gif)

## Atlas space

`napari-brainreg` also comes with an additional plugin, for visualising your data in atlas space, 
i.e., where your data is warped to the atlas coordinate space.

This is typically only used in other software, but you can enable it yourself:

* Open napari
* Navigate to `Plugins` -> `Plugin Call Order`
* In the `Plugin Sorter` window, select `napari_get_reader` from the `select hook...` dropdown box
* Drag `brainreg_read_dir_standard_space` (the atlas space viewer plugin) above `brainreg_read_dir` 
(the normal plugin) to ensure that the atlas space plugin is used preferentially.

