# Docs
This repo is a submodule of `bioimageloader` for documentation. Compile docs using make
and sphinx. Find HTML inside `_build/html/index.html`.

Main repo: https://github.com/LaboratoryOpticsBiosciences/bioimageloader

## Notes
- [IMPORTANT] Separate environment for compiling docs. Follow below instruction.
- Allow only HTML compilation
- Post compilation
    - `modify_table_html.py`: Add necessary tags to `table_maskdataset.html`
    - `add_images_table_html.py`: Add samples images to `table_maskdataset.html`

## Steps
1. Install requirements from `bioimageloader` package. ``pip intall bioimageloader[dev]``

2. (optional) Execute notebook first and save outputs

3. Switch to env for docs

4. Compile docs
    ``` bash
    make html
    ```

- (anytime) Clean docs
    ```bash
    make clean
    ```

## How to update table overview
Table is stored in `_static/table_maskdataset.md` as a Markdown format. Once you added a
new dataset, please update this table accordingly. After that go to
https://www.tablesgenerator.com/ and copy and paste the table to convert it into HTML
format. Download and save it in `_static/table_maskdataset.html.orig`.

Make exactly two sample images in PNG format and save them in `_static/sample_images`.
Set filenames following other examples "`{acronym}_{n_sample}_{ind_sample}.png`".
Normally, it should be enough to write acronym in the filename.

This HTML file will be processed before sphinx-build by `scripts/add_images_table_html.py`
and `scripts/modify_table_html.py`.


## Troubleshooting
- [pandoc](https://pandoc.org/) missing

    `nbsphinx` requires `pandoc`. If you are using `conda`, install it by executing
    `conda install -c conda-forge pandoc`. Otherwise, follow the official documentation
    (https://pandoc.org/installing.html).
