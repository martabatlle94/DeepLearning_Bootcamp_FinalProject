
## Annex I: pipenv (Python)

- Launch an environment: launch a subshell and locate a Pipfile
```bash
pipenv shell
```
- If we want to know from where Python is being executed inside the pipenv environment:
```bash
python # open the python shell
>>> import sys
>>> sys.executable
#'C:\\Users\\David\\.virtualenvs\\pipenv_tests-kta5TH8-\\Scripts\\python.exe'
```

- Or you can know the folder in:
```bash
pipenv --venv
#C:\Users\David\.virtualenvs\pipenv_tests-kta5TH8-
```

- Where the pipenv project is (folder):
```bash
pipenv --where
#D:\Google Drive\25. SaturdaysAI\pipenv_tests
```


### Install package inside the env
```bash
pipenv install camelcase
```

- If we inspect the **Pipfile** (not Pipfile.lock) in that directory we will see:

```sql
/*
[[source]]
name = "pypi"
url = "https://pypi.org/simple"
verify_ssl = true

[dev-packages]

[packages]
camelcase = "*"

[requires]
python_version = "3.7"
*/
```

- The asterisk means it is the latest version. 

- If we look at the **Pipfile.lock** it has all the **dependencies and the dependencies of the dependencies**. This will help us to have a deterministic build so that we will have the same versions when we are ready to deploy. 


### List the packages of the environment

```bash
pipenv lock -r

#-i https://pypi.org/simple
#camelcase==0.2
```

### Uninstall a package
```bash
pipenv uninstall camelcase
```

### Install packages for only developing, NOT in production

```bash
pipenv install nose --dev
```
- In the Pipfile we will see that is added in the dev-packages:

```sql
/*
[dev-packages]
nose = "*"
*/
```

### Install packages from a requirements .txt


```bash
pipenv install -r requirements.txt
pipenv install -r dev-requirements.txt --dev # to install requirements for the dev packages
```

- These packages will be added in the Pipfile and the Pipfile.lock will be also updated. 

- Or from requirements in github account:

```bash
pipenv install -e git+https://github.com/requests/requests.git#egg=requests
```


### Check for security vulnerabilities

```bash
pipenv check
```

- In some cases if a module version has been updated by correcting mistakes for the previous version, if we are using that previous version we will be noticed.

### Change version of package manually

- We can go to the Pipfile and change manually the version of a package. Once we change it we save the file and run:

```bash
pipenv install
# if we add numpy = "==1.18.2" in the packages section and run install we will get this module with that version
```

- This will look at the Pipfile and check if all the versions match the installed versions, and if not, it will update packages. 

### View dependency graph

```bash
pipenv graph
```

### Prepare for production

- Lock the Pipfile.lock:
```bash
pipenv lock
```

- **Once you get in the SERVER were you want to deploy the code, you want the pipenv install to look at the .lock file and ignore the Pipfile**:

```bash
pipenv install --ignore-pipfile
```

- If you want to install the "dev" packages:

```bash
pipenv install --dev
```



### Remove pipenv virutal env

```bash
pipenv --rm
```

### Generate a requirements file from Pipfile

```bash
pipenv lock -r > requirements.txt
```
