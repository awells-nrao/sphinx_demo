
General Workflow for Conversion
===============================

* Create a GitHub repository for Sphinx document-building. Ideally, this will become a part of the CASA Docs readthedocs repository.

* Convert MediaWiki guides to IPython notebooks (.ipynb) with the following:

  .. code-block:: bash

     curl 'https://casaguides.nrao.edu/index.php?title=First_Look_at_Imaging_CASA_6.6.1&action=raw' | pandoc --from=mediawiki --to=gfm -o First_Look_at_Imaging.md && jupytext --to notebook First_Look_at_Imaging.md

* Add the resulting ``.ipynb`` to the ``/docs`` directory of the repository.

* Download photos from the old guides and add to ``/images``.

* Update image links and self-referencing wiki links, such as `[[Extracting_scripts_from_these_tutorials]]` and `{{plotms_6.6.1}}`, within the ``.ipynb``.

* Publish the ``.ipynb`` to HTML with Sphinx using the command ``make html``.

  * We use ``nbsphinx_execute = 'never'`` in ``conf.py`` so that code cells may remain as code in the ``.ipynb`` without being executed.
  * We can also run ``make html SPHINXOPTS=""`` with ``nbsphinx_allow_errors = True`` in ``conf.py`` to let the build complete despite any errors.

.. First Look at Imaging
   =====================

.. toctree::
   :maxdepth: 2
   :caption: ALMA Guides

   first_look_at_imaging.ipynb

