# Python Virtual Environment

### Purpose of Python virtual environment

- To create an isolated environment for different Python projects
  - You can install a specific version of the module on each project without worrying that it will affect your other Python projects.

<br>

<br>

## Create Virtual Environment for Python 3

<br>

> Check your python version

```bash
$ python --version
Python 3.6.9
```

Python 2 까지는 외부패키지를 통해 설치했지만 Python 3 부터는 venv 모듈이 내장되어 있기 때문에 따로 설치할 필요 없습니다. 만약 Python 2 라면

```bash
$ pip install virtualenv
```

<br>

> Create a virtual environment

```bash
$ python -m venv venv
```

<br>

> activate your virtual environment

```bash
$ source venv/bin/activate
```

<br>

> set up command alias in .`bashrc`

```bash
alias va="source venv/bin/activate"
```

<br>