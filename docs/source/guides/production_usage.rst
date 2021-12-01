Using production pipelines
==========================

This page describes how to use a production pipelines to process data.

Production pipelines provide tried and tested bioinformatics workflows
that are ready to be used for processing data sets.
Using the example of `pipeline_rnaseq_hisat2 
<https://github.com/sims-lab/pipeline_rnaseq_hisat2>`_,
this guide demonstrates how to set up and use a production pipeline
for any suitable data set.

Getting started
---------------

Preparing your project on GitHub
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To start, `sign in to GitHub <https://github.com/login>`_
and navigate to the repository of the production pipeline, e.g.
`pipeline_rnaseq_hisat2 <https://github.com/sims-lab/pipeline_rnaseq_hisat2/>`_.
Click the green button :guilabel:`Use this template` to make a working copy
of the pipeline for your project:

* Leave the default "Owner", or change it to something better for a tutorial project.
* Introduce an appropriate "Repository name", for example ``pipeline_rnaseq_tutorial``.
* Feel free to choose whether to make your repository "Public" or "Private".

.. note::

   The template repository includes a GitHub Action workflow for continuous integration,
   which counts towards your GitHub Action usage allowance for private repositories.
   That workflow is only relevant to testing the pipeline during development
   and maintenance. You will not need it for using the pipeline, and a section below
   demonstrates how to disable GitHub Action on your repository.

After that, click on the green :guilabel:`Create repository from template` button,
which will generate a new repository on your personal account
(or the one of your choosing).
This is the repository you will import on Read the Docs,
and it contains the following files and sub-directories:

``.github/workflows/build.yml``
  Sub-directory that contains instructions for GitHub Action workflows,
  you will leave it untouched.

``data/``
  Sub-directory where you will download the FASTQ files for this tutorial.
  In your own projects, we recommend create symbolic links in this folder,
  while keeping your original data files outside of this repository
  (mostly to avoid accidentally committing those files to Git).

``envs/``
  Sub-directory that contains YAML files describing Conda environments
  for running or testing the pipeline, you will leave it untouched.
  You will only used those files as input to create the necessary
  Conda environment on the system where you will run the pipeline.

``etc/``
  Sub-directory that contains additional files needed specifically 
  for continuous integration, you will leave it untouched.

``README.md``
  Basic description of the repository.
  You will edit it as you see fit.

``config.yml``
  YAML file that is used to configure parameters of the pipeline.
  The file is included with example values.
  You will edit this file with values suited to your own situation,
  before running the pipeline.

``pipeline.py``
  Python script that describes the pipeline steps and overall workflow,
  you will leave it untouched.
