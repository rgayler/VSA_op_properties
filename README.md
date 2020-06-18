# VSA operator properties

[Vector Symbolic Architectures](https://github.com/jdblischak/workflowr)
or [Hyperdimensional Computing](https://doi.org/10.1007/s12559-009-9009-8) systems
are computational systems designed in terms of carefully chosen mathematical operators
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

## Project structure

* We are using the [`{workflowr}`](https://github.com/jdblischak/workflowr) package 
to structure the project so that the work is computationally reproducible
and all the materials and outputs are openly accessible.
  * The project code is shared publicly on GitHub at https://github.com/rgayler/VSA_op_properties
  * The website automatically generated from the rendered project documents is at https://rgayler.github.io/VSA_op_properties/

* [`{workflowr}`](https://github.com/jdblischak/workflowr) only manages a subset of the files,
so you will need to manually stage and commit any other files
that need to be mirrored on GitHub.

* There are three key source documents:
  * `analysis/skeleton.Rmd` contains the outline of the final paper
  and meta-level notes about the content of the paper and the simulations to support the paper.
  * `analysis/simulation.Rmd` contains the outline of the final paper
  and meta-level notes about the content of the paper and the simulations to support the paper.
  * `paper/paper.Rmd` contains the final output paper.

* Refer to John Blischak's https://github.com/jdblischak/singleCellSeq 
(created before he developed  [`{workflowr}`](https://github.com/jdblischak/workflowr)) 
for ideas on project organisation.*

## Installation

* All detailed setup instructions and notes go in this project-level `READ.md` file.
  * The `README.md` files in the subdirectories only state the purpose of each directory
and the files in that directory.

## Analysis documents

* There are cross-references between `analysis/skeleton.Rmd` and `analysis/simulation.Rmd`.
  * The only between-file cross-references supported in  [`{workflowr}`](https://github.com/jdblischak/workflowr)
  are the section references implemented by `PanDoc`.
  See https://github.com/jdblischak/workflowr/issues/210
  * Use only user-assigned reference labels (instead of reference labels automatically generated from the section header text),
  so that the section header text can be changed without changing any reference labels that are used, e.g.

    ```
    ## Some text for a section header {#a-user-defined-ref-label}

    As noted in [some other file](#some_other_file_name.htmlsome-other-ref-label)
    ```
  * Only section headers can be cross-referenced like this.
  So everything to be cross-referenced must have a section header with a reference label.

* Bibliography records for the documents in `analysis/`
are manually exported from Zotero and stored in the `analysis/VSA_operators.bibtex`.
  * The same records are used in the output paper.

* The reference style sheet for the documents in `analysis/`
is stored in the `analysis/apa-single-spaced.csl` directory.

* Add `mathjax = "local"` as an argument to `workflowr::wflow_html` in `analysis/_site.yml`
so that the MathJax JavaScript library is bundled with the website in `docs/`
rather than being loaded from a remote server when the website is viewed.
This removes the dependency on the rempte server being available.
See https://github.com/jdblischak/workflowr/issues/211

  ```
  output:
    workflowr::wflow_html:
      mathjax: "local"
  ```

## Output paper

The output paper is not managed by [`{workflowr}`](https://github.com/jdblischak/workflowr),
so needs manual management with respect to `git`.

* Most files for creation of the output paper are in the `paper/` directory.
  * This directory was created by the [`{rticles}`](https://CRAN.R-project.org/package=rticles) package,
  using the `PeerJ` template.
  (This will change if we find a different publication venue for the paper.)
  * Any data objects and figures created by the simulation notebook
  for use in the output paper
  are stored in the `output/` directory.

* The output paper (`paper.pdf`) is created in the `paper/` directory,
but needs to also exist in the `docs/` directory
so that it can be referenced from the web pages (locally and on GitHub).
See https://github.com/jdblischak/workflowr/issues/209
  * After creating `paper.pdf` for the first time,
  move the file form `paper/` to `docs/`,
  open a terminal, change directory to `paper/`,
  and manually create a symlink to the file (`ln -s ../docs/paper.pdf paper.pdf`).
  *The file needs to be in `docs/` so that GitHub picks it up for rendering the GitHub pages.
  When the paper is regenerated, it is written to the symlink in `paper/`,
  which updates the file in `docs/`.
  
* Bibliography records are manually exported from Zotero and stored in the `analysis/VSA_operators.bibtex`.
  * `paper/paper.Rmd` directly accesses `analysis/VSA_operators.bibtex`.

*I am not convinced that managing the output paper via GitHub is the best method for remote collaboration
because of the need to merge the individual contributions.
On the other hand, using something like Overleaf for editing the source text
would not allow executable code in the text
and would have the problem of synchronising output objects with the Overleaf environment.*
  
## To do

* Decide whether to binderise the repository. See https://mybinder.org/

* Sort out the sparate licensing for code and text.

* On completion write up the relevant bits of the project structure to contribute to the `{workflowr}` documentation.
