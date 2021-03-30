# Python Virtual Environment

> Ref: [Chloe's TIL](https://chloe-codes1.gitbook.io/til/python/python_virtual_environment)

### Purpose of Python virtual environment

* To create an isolated environment for different Python projects
  * You can install a specific version of the module on each project without worrying that it will affect your other Python projects.

## Create Virtual Environment for Python 3

1. Check your python version
   * ```text
     $ python --version
     Python 3.6.9
     ```
   * > Python 2 까지는 외부패키지를 통해 설치했지만 Python 3 부터는 venv 모듈이 내장되어 있기 때문에 따로 설치할 필요 없습니다. 만약 Python 2 라면 아래 명령을 통해 패키지를 설치합니다.

     * ```text
       $ pip install virtualenv
       ```
2. Create a virtual environment
   * ```text
     $ cd < 프로젝트 디렉토리 >
     $ python -m venv .venv
     ```
3. git ignore

   > 가상 환경을 굳이 Git과 같은 소스 버전 관리 시스템에 올릴 필요는 없으므로 `.venv` 디렉토리를 `.gitignore` 파일에 추가

   * ```text
     $ echo '.venv' >> .gitignore
     ```

4. activate your virtual environment
   * ```text
     # mac
     $ source .venv/bin/activate
     ```
   * ```text
     # mac
     $ source .venv/Script/activate
     ```
5. set up command alias in .`bashrc`
   * ```text
     alias va="source venv/bin/activate"
     ```

## Caution

1. 파이썬버전에 따라서 생성된 activate 파일의 확장자가 .bat 일 수 있다.
   * .bat 파일은 powershell 이나 bash 에서 실행되지 않고 cmd에서만 작동한다.
   * ```text
     $ source .venv/bin/activate.bat
     ```

