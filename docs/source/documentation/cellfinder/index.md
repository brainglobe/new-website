# cellfinder

cellfinder is software for automated 3D cell detection in very large 3D images (e.g., serial two-photon or lightsheet 
volumes of whole mouse brains).

![Detected labelled cells, overlaid on a segmented coronal brain section](images/cells.png)
**Detected labelled cells, overlaid on a segmented coronal brain section**

## Ways to use cellfinder
cellfinder exists as three separate software packages with different user interfaces and different aims.

:::{hint}
If you don't know how to start, we recommend the cellfinder napari plugin. 
:::


### cellfinder-core
`cellfinder-core` is a Python package implementing the core algorithm for efficient cell detection in large images.

The package exists on its own to allow developers to implement the algorithm in their own software. For now, the only 
API documentation is in the [GitHub README](https://github.com/brainglobe/cellfinder-core/blob/main/README.md), please 
see the documentation for the napari plugin [here](user-guide/napari-plugin/index) for an explanation of the parameters. 
Alternatively, please [get in touch](/contact).

### cellfinder napari plugin

This is a thin wrapper around the `cellfinder-core` package and aims to:

* Provide the cell detection algorithm in a user-friendly form
* Allow the cell detection algorithm to be chained together with other tools in the Napari ecosystem
* Allow easier parameter optimisation for users of the other cellfinder tools.


![Visualising detected cells in the cellfinder napari plugin](images/napari-cellfinder.gif)
**Visualising detected cells in the cellfinder napari plugin**

### cellfinder command-line tool
A command-line tool (confusingly just called `cellfinder`) exists to combine the `cellfinder-core` cell detection 
algorithm and [brainreg](/documentation/brainreg/index). `cellfinder` can:

* Detect labelled cells in 3D in whole-brain images (many hundreds of GB)
* Register the image to an atlas (such as the [Allen Mouse Brain Atlas](https://atlas.brain-map.org/atlas?atlas=602630314))
* Segment the brain based on the reference atlas
* Calculate the volume of each brain area, and the number of labelled cells within it
* Transform everything into standard space for analysis and visualisation


## Installation
```{toctree}
:maxdepth: 1
installation
```

## User guide
```{toctree}
:maxdepth: 1
user-guide/command-line/index
user-guide/napari-plugin/index
user-guide/cellfinder-core
user-guide/training-strategy
troubleshooting/index
```

## Tutorials
```{toctree}
:maxdepth: 1
/tutorials/cellfinder-cli/index
```


## Citing cellfinder

If you find cellfinder useful, and use it in your research, please cite the paper outlining the cell detection algorithm:
> Tyson, A. L., Rousseau, C. V., Niedworok, C. J., Keshavarzi, S., Tsitoura, C., Cossell, L., Strom, M. and Margrie, T. W. (2021) “A deep learning algorithm for 3D cell detection in whole mouse brain image datasets’ PLOS Computational Biology, 17(5), e1009074
[https://doi.org/10.1371/journal.pcbi.1009074](https://doi.org/10.1371/journal.pcbi.1009074)
>
If you use any of the image registration functions in cellfinder, please also cite [brainreg](/documentation/brainreg/index).
