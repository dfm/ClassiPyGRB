![Logo](docs/Animations/images/logo.jpeg)  

**ClassiPyGRB** is a Python 3 package to download, process, visualize, and classify Gamma-Ray-Bursts (GRBs) from the Swift/BAT Telescope (https://swift.gsfc.nasa.gov/about_swift/bat_desc.html) database. It is distributed over the GNU General Public License Version 2 (1991). Please read the complete description of the method and its application to GRBs in this [publication](JOSS_Docs/paper.md).
# Statement of need
The Swift Burst Alert Telescope (BAT) is a wide-field, hard Gamma-ray detector that, since its launch in 2004, has played an important role in the high-energy astrophysical field. A preliminary query on the Astrophysics Data System (ADS) with the keyword "Swift/BAT" indicates that over 7000 research works have been uploaded to its platform (up to December 2023). Furthermore, recently has been increased the number of studies per year, evidencing the relevance and impact of the use of the Swift/BAT database.

Although the Swift/BAT database is [publicly available](https://swift.gsfc.nasa.gov/results/batgrbcat/), for first-time users it might be a challenge to download and process the data. The data is stored in multiple directories, depending on the GRB. Moreover, the data is not pre-processed, and the user must perform the data manipulation and interpolation by themselves. These issues make the data processing a time-consuming task. **ClassiPyGRB** is a Python 3 package that aims to solve these problems by providing a simple and intuitive interface to download, process, visualize, and classify the photometric data of GRBs from the Swift/BAT database.

**ClassiPyGRB** allows researchers to query light curves for any GRB in the Swift/BAT database simply and intuitively. The package also provides a set of tools to preprocess the data, including noise/duration reduction and interpolation. Moreover, The package also provides a set of facilities and tutorials to classify GRBs based on their light curves, following [Jespersen et al.(2020)](https://doi.org/10.3847/2041-8213/ab964d) and [Garcia-Cifuentes et al.(2023)](https://doi.org/10.3847/1538-4357/acd176). This method is based on a dimensionality reduction of the data using t-Distributed Stochastic Neighbour Embedding (TSNE), where the user can visualize the results using a Graphical User Interface (GUI). The user can also plot and animate the results of the TSNE analysis, allowing to perform a deeper hyperparameter grid search. The package is distributed over the GNU General Public Licence Version 2 (1991).

# Attribution
If you use this code in a publication, please refer to the package by its name and cite [Garcia-Cifuentes et al.(2023)](https://doi.org/10.3847/1538-4357/acd176) -> [Astrophysical Journal Vol. 951 No. 1](https://doi.org/10.3847/1538-4357/acd176). Any question, please email [Keneth Garcia-Cifuentes](mailto:kenet.garcia@correo.nucleares.unam.mx).

# Dependencies and Installation

This repository requires Python 3.8 or high, and a list of packages downloaded automatically ([numpy](https://github.com/numpy/numpy), [scikit-learn](https://scikit-learn.org/stable/index.html), etc.). In addition, it is required to install all the dependencies related to Tkinter, Pillow, and ImageTK. There are some options to download it, but we recommend two in the next sections.

>[!IMPORTANT]
> The next instructions requires knowledge of conda/mamba environments and Linux/Git management systems. You can use integrated development environments (IDEs) such as PyCharm or Visual Studio Code to reduce the effort of installing ClassiPyGRB (i.e., PyCharm has an integrated workflow to create new environments without a terminal).

### Using Mamba/Conda
`Conda` and `Mamba` are package management tools for creating, sharing, and managing environments and software across different platforms in Python. You can use ClassiPyGRB on both Mamba and Conda with a new/existing environment compatible with Pillow.

>[!NOTE]
> In Mamba, you can create a new environment following:
>```
>$ mamba create -n ClassiPyGRB -c conda-forge python=3.10 pytables=3.8.0 pillow
>$ mamba activate ClassiPyGRB
>```

>[!NOTE]
> In Conda, you can create a new environment using a similar approach:
>```
>$ conda create -n ClassiPyGRB -c conda-forge python=3.10 pytables=3.8.0 pillow
>$ conda activate ClassiPyGRB
>```

>[!TIP]
> Some notes about the previous commands:
>- Using Pillow as a dependency in the conda/mamba environment is optional. If your current operative system has an installation of `imagetk`, you can omit this requirement. 
>- The Python version selected for your conda/mamba environment depends on your current OS. You can check the available versions by running `conda search python` or `mamba search python` (but use `python>=3.8`).
>- The `pytables` package is required to manage data on hdf5 files. If you have the appropriate hdf5 dev library installed on your OS, you can omit this requirement (see more details [here](https://www.pytables.org/usersguide/index.html)).

### Debian-based Linux distributions
Another option is to install the dependencies directly on your current Linux distribution. In Debian-based distros, you can install these packages by running the following commands:

```
$ sudo apt-get install python3-tk
$ sudo apt-get install python3-pil python3-pil.imagetk
```

Other data management packages such as [Numpy](https://numpy.org/) or [Pandas](https://pandas.pydata.org/) will be required in Documentation.

>[!TIP]
> You can set up **ClassiPyGRB** dependencies on other Linux distributions by installing the previous packages in your operating system and following the next steps. The procedure changes between distributions, and therefore a more cross-platform option would be conda/mamba environments. If you have a specific incompatibility on your OS, you can create an issue and contribute to ongoing improvements and enhancements. Your feedback is appreciated!

## Installing **ClassiPyGRB**

At this point, it is possible to install **ClassiPyGRB** on Mamba/Conda and Linux distributions. In both cases, we assume that you have already installed the dependencies and the appropriate Python version. Now, there are two options to install **ClassiPyGRB**:

>[!IMPORTANT]
> If you are not using a conda/mamba environment, it is strongly recommended to use a virtual environment to install **ClassiPyGRB**. Installing packages globally on your OS can cause conflicts with other packages and dependencies. You can use [virtualenv](https://virtualenv.pypa.io/en/latest/) or [venv](https://docs.python.org/3/library/venv.html) to create a virtual environment. Some IDEs such as PyCharm or Visual Studio Code have integrated workflows to create virtual environments.

### GitHub

You can install the latest sources from **ClassiPyGRB** by cloning the repository directly from GitHub:
```
$ git clone https://github.com/KenethGarcia/ClassiPyGRB
$ cd ClassiPyGRB
$ pip install .
```
Or, instead, use `pip` with the path to the repository:
```
$ pip install ClassiPyGRB@git+https://github.com/KenethGarcia/ClassiPyGRB
```

### PyPI
A stable compiled version of **ClassiPyGRB** is available on [PyPI](https://pypi.org/). You can install it by running:
```
$ pip install ClassiPyGRB
```

## Testing

If you have installed the development version of **ClassiPyGRB** or cloned the complete source code (e.g., from the GitHub repository), you can run the tests by executing the following commands:

```
$ cd ClassiPyGRB
$ python -m unittest -v
```


# Features

In **ClassiPyGRB**, it is possible to retrieve data from the Swift/BAT catalog by a three-line code:
```
from ClassiPyGRB import SWIFT
swift = SWIFT(res=64)
df = swift.obtain_data(name='GRB211211A')
```
Moreover, you can plot a light curve using one single line of code:
```
swift.plot_any_grb(name='GRB060614')
```
You can do specialized tasks to see the convergence of t-distributed Stochastic Neighbor Embedding (TSNE):

![convergence](docs/Animations/animation1.gif)

Or use a Graphical User Interface (GUI) to analyze the embeddings obtained by TSNE:

![GUI](docs/Animations/images/Use.png)

We strongly encourage you to read the Tutorials of **ClassiPyGRB** before starting. This documentation includes all the details and follow-up for managing and processing data from Swift/BAT, performing TSNE, plotting and animating their results, and how to use the internal GUI.
Moreover, we developed intuitive notebooks to support you in your research.

- 1. [Basic Usage](docs/1.Basic_Usage.ipynb)
		
- 2. [BAT: Data_Download](docs/2.BAT_Data_Download.ipynb)
	
- 3. [BAT: Preprocess](docs/3.BAT_Preprocess.ipynb)
	
- 4. [BAT: Noise_Reduction](docs/4.BAT_Noise_Reduction.ipynb)
	
- 5. [BAT: Interpolation](docs/5.BAT_Interpolate.ipynb)
	
- 6. [TSNE: Introduction](docs/6.TSNE_Introduction.ipynb)
	
- 7. [TSNE: Overview](docs/7.TSNE_Overview.ipynb)
	
- 8. [Plotting with t-SNE](docs/8.TSNE_Plotting.ipynb)
	
- 9. [Clustering Properties](docs/9.Cluster_Properties.ipynb)

- 10. [Applications and Example](docs/10.Extended_Emission.ipynb)

- 11. [Internal GUI](docs/11.Viewer_Instance.ipynb)

# Enhancement and Support

**ClassiPyGRB** is an open-source package where all kinds of contributions are welcome. Whether you want to report a bug or submit a pull request, your feedback, comments, and suggestions will be very welcome.

Here are some ways you can get involved in this project:
- Report a bug or issue on our [GitHub Issues](https://github.com/KenethGarcia/ClassiPyGRB/issues) page.
- Suggest a new feature or improvement by opening a new issue.
- Submit a [pull request](https://github.com/KenethGarcia/ClassiPyGRB/pulls) with your code changes or enhancements.
- Share ClassiPyGRB on social media or with your colleagues.

We appreciate your interest in this package. Please do not hesitate to email [Keneth Garcia](mailto:keneth.garcia@correo.nucleares.unam.mx) to discuss any topic related to **ClassiPyGRB**.