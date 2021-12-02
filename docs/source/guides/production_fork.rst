Developing production pipelines
====================================

This guide describes how to obtain a copy of a production pipeline
with the intention to edit it and contribute the changes back to the
parent repository.
To develop a whole new pipeline from scratch, refer to :doc:`/guides/template`.

Production pipelines are subject to change over time,
following updates to dependencies and best practices in the field.
Contributions to production pipelines can be made directly on the repository,
or through pull requests from forks of the repository.

Getting started
---------------

Preparing your project on GitHub
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To start, `sign in to GitHub <https://github.com/login>`_
and navigate to the repository of the production pipeline, e.g.
`pipeline_rnaseq_hisat2 <https://github.com/sims-lab/pipeline_rnaseq_hisat2/>`_,
where you will see a grey button :guilabel:`Fork` in the top-right corner of the page.

* Click it to open a modal window that will ask you where you want to fork that repository.
* Select your GitHub username, or something suitable for a tutorial project.

This will generate a new repository on your personal account
(or the one of your choosing).
This is the repository you will use to work on the pipeline and prepare pull requests
to the parent repository, and it contains the following files and sub-directories:

``.github/workflows/build.yml``
  Sub-directory that contains instructions for GitHub Action workflows,
  you will leave it untouched.

``data/``
  Sub-directory where you will download the input FASTQ files for this guide.
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

.. figure:: /_static/images/guides/github-fork.png
   :width: 80%
   :align: center
   :alt: Production pipeline forked on GitHub

   Production pipeline forked on GitHub

First steps
-----------

Triggering the first build
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: /_static/images/guides/github-workflow-enable.png
   :width: 80%
   :align: center
   :alt: View before enabling GitHub Action runs.

   View before enabling GitHub Action runs

GitHub will automatically detect GitHub Action workflows
in your project, but on forked repositories it requires you to explicitly
allow them to run, for security reasons.

Click on the green button :guilabel:`I understand my workflows, go ahead and enable them`.
This will take you to the "Actions" page of the repository,
where you will find the list of workflows (one workflow) and workflow runs (empty so far).

* Click on the workflow :guilabel:`CI`, in the left pane.
* On the right, click on the grey button :guilabel:`Run workflow`,
  leave ``main`` as the selected branch,
  and click on the green button :guilabel:`Run workflow`.

.. figure:: /_static/images/guides/github-action-manual-run.png
   :width: 80%
   :align: center
   :alt: View before enabling GitHub Action runs.

   View before enabling GitHub Action runs

After a few seconds, an entry will appear in the main panel,
representing the first run of the workflow.

To see the build logs, click on the title of the workflow run.

.. figure:: /_static/images/guides/fork-first-successful-build.png
   :width: 80%
   :align: center
   :alt: First successful build

   First successful build
