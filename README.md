# guide-for-creating-workflows

Workflows are all things that can be computed, broadly speaking. 

For reproducibility, we want our workflows to be repeatable: producing the same output every time they are computed. 
This is easy enough to do in first approximation, but might be harder to achieve than it seems when the workflow relies on external resources. But we track every execution so it is not necessary to be overly concerned about these delicate details at every moment.

Generally, we want the workflows to be parametrized. Non-parametrized but strickly repeatable notebooks are equivalent to their output data.

One way to create them in ODA is to build **jupyter notebook**.

## Guide to a simple ODA Jupyter Notebook workflow


* write your notebook, and make sure it runs from top to bottom
* make a requirements.txt will the modules you need for this notebook
* parameterize the notebook, by creating cell with the following tag "parameters" (see [papermill manual](https://papermill.readthedocs.io/en/latest/usage-parameterize.html#designate-parameters-for-a-cell)):
* define the notebook output, similarly creating cell with tag "outputs". 
  * outputs may be strings, floats, lists
  * outputs may be also strings which contain filenames for valid files. If they do, the whole file will be considered output.
* install nb2workflow tooling `pip install nb2workflow[cwl,oda] --upgrade`
* inspect the notebook `nbinspect my-notebook.ipynb`
* try to run the notebook `nbrun my-notebook.ipynb`
  * it will use all default parameters 
  * you can specify parameters as `nbrun --inp-nbins=10 my-notebook.ipynb`, if `nbins` happens to be one of the parameters.
* try to start the service `nb2service my-notebook.ipynb`
