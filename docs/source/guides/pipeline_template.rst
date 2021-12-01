Working with the template pipeline
==================================

This page describes how to work with the template pipeline,
`pipeline_template <https://github.com/sims-lab/pipeline_template/>`_.

Getting started
---------------

Preparing your project on GitHub
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To start, `sign in to GitHub <https://github.com/login>`_
and navigate to `the template pipeline <https://github.com/sims-lab/pipeline_template/>`_,
where you will see a green :guilabel:`Use this template` button.
Click it to open a new page that will ask you for some details:

* Leave the default "Owner", or change it to something better for a tutorial project.
* Introduce an appropriate "Repository name", for example ``pipeline_tutorial``.
* Make sure the project is "Public", rather than "Private".

.. note::

   The template repository includes a GitHub Action workflow for continuous integration.
   Public repositories do not have any usage limit on GitHub Action, but private repositories do.

After that, click on the green :guilabel:`Create repository from template` button,
which will generate a new repository on your personal account
(or the one of your choosing).
This is the repository you will import on Read the Docs,
and it contains the following files and sub-directories:

``.github/workflows/build.yml``
  Sub-directory that contains instructions for GitHub Action workflows.
  You will need to edit this file with instructions specific to each pipeline
  that is derived from the template (e.g., download test files,
  name of the Conda environment).

``envs/``
  Sub-directory that contains YAML files describing Conda environments
  for running or testing the pipeline.
  You will edit those files as you develop the pipeline,
  to provide all the dependencies that are needed for
  the GitHub Action workflow and end-users.

``etc/``
  Sub-directory that contains additional files needed specifically 
  for continuous integration, you will leave it untouched.

``README.md``
  Basic description of the repository.
  You will edit it as you see fit.

``config.yml``
  YAML file that is used to configure parameters of the pipeline.
  You will edit this file as you develop the pipeline,
  to provide a template and default values that can be edited by users
  for each run of the pipeline.

``pipeline.py``
  Python script that describes the pipeline steps and overall workflow.
  You will edit this file as you develop the pipeline,
  adding new tasks, importing new modules, and managing the overall 
  workflow feeding the output of some task as the input to others.

.. figure:: /_static/images/guides/github-template.png
   :width: 80%
   :align: center
   :alt: GitHub template for the tutorial

   Template pipeline on GitHub

First steps
-----------

Checking the first build
~~~~~~~~~~~~~~~~~~~~~~~~

GitHub will automatically try to run the GitHub Action workflows
of your project right after you create it.
To see the build logs, click on the orange circle icon next to
the commit ID on the project repository,
or alternatively navigate to the "Action" page,
then open the one on top (the most recent one).

If the build has not finished yet by the time you open it,
you will see a yellow indicator, meaning that it is still
in progress. However, even the logs of builds in progress
can be viewed as they are being produced.

.. figure:: /_static/images/guides/template-first-successful-build.png
   :width: 80%
   :align: center
   :alt: First successful build

   First successful build
