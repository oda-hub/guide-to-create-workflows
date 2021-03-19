# guide-to-create-workflows

Workflows are things that can be computed, broadly speaking. One way to create them in ODA is to build **jupyter notebook**.

For reproducibility, we want our workflows to be repeatable: producing the same output every time they are computed. 
This is easy enough to do in first approximation, but might be harder to achieve than it seems when the workflow relies on external resources. But we track every execution so it is not necessary to be overly concerned about these delicate details at every moment.

Generally, we want the workflows to be parametrized. Non-parametrized but strickly repeatable notebooks are equivalent to their output data.


## Guide to a simple ODA Jupyter Notebook workflow


* parameterize the noteboo
