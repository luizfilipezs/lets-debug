For uploading this package, follow these instructions:

- Change the version number in `setup.py`
- Run setup file again. `python setup.py bdist_wheel`
- Upload only that dist file or run twine (if using). `twine upload --skip-existing dist/*`