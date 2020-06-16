# VSA operator properties

[Vector Symbolic Architectures](https://github.com/jdblischak/workflowr)
or [Hyperdimensional Computing](https://doi.org/10.1007/s12559-009-9009-8) systems
are computational systems designed in terms of carefully chosen operators
applied to high-dimensional vector spaces.
VSAs appear to be robust to a wide range of choices of the specific vector space and operators.
This raises the question of which properties are required for VSAs
and how those relate to the choices of vector space and operators.

In this project we construct a reasonable parameterisation of VSA operators
and map out the algebraic properties of VSA operators
as a function location in the parameter space.
To the extent that the practical uitility of VSA operators
follows from their algebraic properties,
this map will help in understanding and designing VSA computational systems.

This project is the joint work of (alphabetically):

* [Charles T. Gray](https://www.linkedin.com/in/charles-gray-mathbassador/)
* [Ross W. Gayler](https://www.rossgayler.com/)
* [Stefan Reimann](https://www.linkedin.com/in/stefanreimann/)

# Project structure

We are using the `{[workflowr](https://github.com/jdblischak/workflowr)}` package 
to structure the project so that the work is computationally reproducible
and all the materials and outputs are openly accessible.

**Refer to John Blischak's https://github.com/jdblischak/singleCellSeq for ideas on project organisation.**

**On completion write up the relevant bits of the project structure for John Blischak at `{workflowr}`.**

# Installation

*Instructions yet to be written.*

All detailed instructions should probably go here,
with the directory-specific` README.md` files only giving the purpose of each directory.

## Analysis documents

* Add `mathjax = "local"` as an argument to `workflowr::wflow_html` in `analysis/_site.yml`
so that the MathJax JavaScript library is bundled with the website in `docs/`
rather than being loaded from a remote server when the website is viewed.
This removes the dependency on the rempte server being available.

  ```
output:
  workflowr::wflow_html:
    mathjax: "local"
  ```

* Bibliography records for the documents in `analysis/`
are manually exported from Zotero and stored in the `analysis/` directory.
* The reference style sheet for the documents in `analysis/`
is stored in the `analysis/` directory.

**NOTE: `{workflowr}` only manages a subset of the files,
so that you will need to manually stage and commit the other files
that need to be mirrored on GitHub.**

## Output paper

The output paper is not managed by {workflowr},
so needs some separate handling.

* Files for creation of the output paper are in the `paper/` directory.
  * This directory was created by the `{[rticles](https://CRAN.R-project.org/package=rticles)}` package,
  using the `PeerJ` template.
  (This will change if we find a different publication venue for the paper.)
  * The paper uses data objects and figures created by the simulation notebook
  and stored in the `output/` directory.

The output paper (`paper.pdf`) is created in the `pape/` directory,
but needs to also exist in the `docs/` directory
so that it can be referenced from the web pages (locally and on GitHub).

* After creating `paper.pdf` for the first time,
move the file form `paper/` to `docs/`,
open a terminal, change directory to `paper/`,
and manually create a symlink to the file (`ln -s ../docs/paper.pdf paper.pdf`).

The file needs to be in `docs/` so that GitHub picks it up for rendering the GitHub pages.
When the paper is regenerated, it is written to the symlink in `paper/`,
which updates the file in `docs/`.

I am not convinced that managing the output paper via GitHub is the best method for remote collaboration
because of the need to merge the individual contributions.
On the other hand, using something like Overleaf for editing the source text
would not allow executable code in the text
and would have the problem of synchronising output objects in the Overleaf environment.
  
* Bibliography records are manually exported from Zotero and stored in the `paper/` directory.

## Binder

*Yet to be decided whether to binderise the repo.*

