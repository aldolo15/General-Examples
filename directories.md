# Directories in Jupyter Notebook

## CWD

```python
import os

# define directories
cwd = os.getcwd()
```

## Parent Directory

```python
cwd             = os.getcwd()
os.chdir('..')
par_dir         = os.path.abspath(os.curdir)
```

## Parent Directory (multiple levels)

```python
cwd             = os.getcwd()
os.chdir('..')
dir_2017        = os.getcwd()
os.chdir('..')
par_dir         = os.path.abspath(os.curdir)
```
## GitHubPath (`os`)

In:
```python
import os
cwd = os.getcwd().replace('\\','/')
print(cwd)
```
Out:
```
C:/Users/<id>/Documents/GitHub/Valuations/Scripts
```

We want just `C:/Users/<id>/Documents/GitHub/`, which we get using this:

In:
```python
import os
cwd = os.getcwd().replace('\\','/')
GitHubPath = cwd[:cwd.find('GitHub/')+len('GitHub/')]
print(GitHubPath)
```

Out:
```
C:/Users/<id>/Documents/GitHub/
```

## GitHubPath (`Pathlib`)
Pathlib is  helpful because it works across operating systems.

In:
```python
>>> from pathlib import Path
>>> print(Path.cwd())
```
Out:
```
/Users/matthewkudija/Documents/GitHub/Aircraft-Data/Utilization/Scripts
```

We want the root GitHub directory `/Users/matthewkudija/Documents/GitHub/`, which we get using this:

In:
```python
from pathlib import Path
cwd = Path.cwd()
for parent in cwd.parents:
  if str(parent)[-6:]=='GitHub':
    GitHubPath = parent

print('GitHubPath:        {}'.format(GitHubPath))
print('Type GitHubPath:   {}'.format(type(GitHubPath)))
```

Out:
```
GitHubPath:        /Users/matthewkudija/Documents/GitHub
Type GitHubPath:   <class 'pathlib.PosixPath'>```


