This folder contains scripts to prepare connectivity matrix input files for a d3 visualization with myconnectome_d3.

# Input Data Format
There are currently TWO input data files- one for all the connections, and one for the nodes.  Both are csv files, with the "connections" file having the following column names:
  "x1","y1","z1","hemisphere1","network1","network_id1","image1","mdsx1","mdsy1","color1","x2","y2","z2","hemisphere2","network2","network_id2","image2","mdsx2","mdsy2","color2","corr"

The nodes file has the following column names:

"x","y","z","hemisphere","network","network_id","image","mdsx","mdsy","color"

You can generate this file however you want, however we provide a script `make_mybrain_json.R` that will take as input a connectivity matrix and meta data, and will help you generate the above.  You should source this script and run it with `run_make_mybrain_json.R` to produce the data files for the web/data folder. There currently isn't sufficient documentation for the meta data file for the input data, so for now just figure it out from the script :)  It's mostly the fields above, minus the multidimensional scaling (MDS) calculations, and the colorings.

# Prepare Your Data
1. You need to prepare the following files:
meta.txt: should be a tab separated file of meta data with the following columns
  - x: the x coordinate of the roi
  - y: the y coordinate of the roi
  - z: the z coordinate of the roi
  - hemisphere: specify "L" or "R"
  - network_name:
  - network_number:

2. connectivity_matrix.txt: a space separated NxN connectivity matrix, with no column or row labels.  These rows and columns ordering should correspond to the rows in the file above.

# make_mybrain_json.R
This script will combine your data and meta data files into one two csv files that will be used for the d3 - the meta data of each node is attached to the node in this file, as are the neighbors.  This script will NOT threshold the data - all connections are included, to be thresholded in the web interface.  This script should be run with

# run_make_mybrain_json.R
See the script for details.
