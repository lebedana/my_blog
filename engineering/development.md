# Development

* Dokumentace - priorita vysoka, zpusobu jsou k tomu prestoupit jsou mraky, je potreba si vytvorit predstavu co vsechno mame k dispozice a ktera varianta nam sedi vice
* [https://github.com/fastai/nbdev](https://github.com/fastai/nbdev) ktery pouziva Tom: \(1\) podporuje hlavne vyvoj v jn \(2\) umi hezky vygenerovat dokumentaci \(vcetne obrazku, tabulek..\) a moznosti si zdrojak otevrit v google colab \(3\) super je taky ze doc pak obsahuje jak text, tak i ukazky kodu, test uatd - Tom doporucuje se podivat na [I Like Notebooks](https://www.youtube.com/watch?v=9Q6sLbz37gk&ab_channel=JeremyHoward) od Jeremy Howard, pro prehled o vyvoji v jn a jejich soucastnych moznostech
* MLOps framework: monolit vs mnozina mensich libek - druha varianta ma spoustu vyhod \(e.g. inspirace [fastai](https://github.com/fastai)\) - budeme pokracovat v patek

The setup: 

* Jeremy Howard vs Joel Grus

Notebooks \(+nbdev\)

* Supports literate programming \(code + doc\) 
* Exploratory programming - programming as a journal 
* Autocomplete \(with definite type, if a cell was executing\) 
* Linting 

[fastai](https://github.com/fastai)

* fastdoc - write a book in jupyer notebooks
* fastpages - jn for blogging  
* [nbdev](https://github.com/fastai/nbdev) - template for Python framewowks 

  * `notebooks2scritpt()` - convert notebooks to 
  * or `nbdev_build_lib`
  * can automatically create hyperlinks with \`\`
  * Doc is nice
  * nbdev\_build\_docs - can be added to CI/CD

Other tools for docs:

* [https://www.sphinx-doc.org/en/master/](https://www.sphinx-doc.org/en/master/)
  * see highlights 
  * result HTML, host anywhere 
* [https://squidfunk.github.io/mkdocs-material/](https://squidfunk.github.io/mkdocs-material/)
  * Generate a doc from markdown
  * Automatically extracts the docstrings \(Google style, [example](https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html)\)
  * Good overview with many broken links - [https://medium.com/@chrieke/documenting-a-python-package-with-code-reference-via-mkdocs-material-b4a45197f95b](https://medium.com/@chrieke/documenting-a-python-package-with-code-reference-via-mkdocs-material-b4a45197f95b)
  * Host e.g. on github pages \(there is function to deploy the doc\)
  * Primary to host on gitlab or github pages 

Docstrings:

* \(so-called\) [NumPy style](http://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_numpy.html) docstrings.
* \(so-called\) Google style, [example](https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html)

Q: 

* Pytourch 
* mypy
* Ne flask ---&gt; [fast API](https://github.com/tiangolo/fastapi) \(podivat se dokumentaci\)
* Pedantic - [https://github.com/samuelcolvin/pydantic/](https://github.com/samuelcolvin/pydantic/) - zajimava dokumentace - a zajimavy fram





