## Encoding a mesh as two DataFrames

The input file in the .off format is converted to two DataFrames using the Convert_TIN_DataFrames_Pure_Spark.ipynb program.
* Inputs:
  - a .off file representing a TIN, e.g., Canyon_Lake_Gorge_TX.off
* Outputs:
  - two .csv files corresponding to the DataFrames $DF_V$ and $DF_T$


## Deriving connectivity relations
The Compute_VT_VV_VE_relations_Pure_Spark.ipynb file is used to compute the VT, VV, and VE relations. The Compute_EV_ET_relations_Pure_Spark.ipynb is used to compute the EV and ET relations.
* Inputs:
  - the DataFrame $DF_T$
* Outputs:
  - a .parquet file in Spark, which is used to store the derived DataFrame corresponding to the desired connectivity relation.

## Computing topological features

### Forman gradient
The Compute_Forman_Pure_Spark.ipynb is used to compute the Forman gradient in a mesh.
* Inputs:
  - the DataFrames $DF_V$ and $DF_T$
* Outputs:
  - a DataFrame storing critical simplices and simplex pairs in a mesh.
 
### Two auxiliary graphs 
The Compute_Two_Graphs_Pure_Spark.ipynb is used to compute two auxiliary graphs from the Forman gradient.
* Inputs:
  - the DataFrames $DF_V$ and $DF_T$
* Outputs:
  - two auxiliary graphs. Each graph is represented by two DataFrames corresponding to nodes and arcs.

### Morse 2-manifolds
The Compute_2-manifolds_Pure_Spark.ipynb is used to compute Morse 2-manifolds.
* Inputs:
  - the graph $G_{VE}$ or $G_{ET}$
* Outputs:
  - ascending or descending 2-manifolds, which are represented by a DataFrame called $result\\_{con}$

### Morse 1-manifolds
The Compute_1-manifolds_Pure_Spark.ipynb is used to compute Morse 1-manifolds.
* Inputs:
  - the graph $G_VE$ or $G_ET$
* Outputs:
  - ascending or descending 1-manifolds, which are represented by a DataFrame.
