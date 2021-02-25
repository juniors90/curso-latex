```
echo "# curso-latex" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/juniors90/curso-latex.git
git push -u origin main
```

- [Yes You Can Use GitHub Pages with Python Sphinx](https://www.docslikecode.com/articles/github-pages-python-sphinx/)

1. Create a new branch locally, named docs-config in this example, based on master:
```
$ git checkout -b docs-config
```
2. Create an empty dot file, named ```.nojekyll``` within the /docs folder of your repo. A dot file has a period prefix and may not be visible in all text editors or your Finder windows, so be aware and don’t panic if you can’t “see” it later.
3. Use the add command to make sure Git starts tracking the file:
```
(venv) $> git add docs/.nojekyll
```
4. Commit the change with the ```-a``` option to add new files to the commit, and the -m option for a message:
```
(venv) $> git commit -a -m "Adds a .nojekyll file for docs builds"
```
5. Push the change to the remote, in this case named “origin”, so you can compare the change to master.
```
(venv) $> git push origin docs-config
```
6. On the GitHub website, go to your repository and create a Pull Request.
7. Merge the Pull Request to add the ```.nojekyll``` file to the master branch.