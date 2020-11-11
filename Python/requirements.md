# requirements.txt

> 파이썬으로 프로젝트를 진행하다보면 pip 으로 여러 패키지를 설치하는데, 프로젝트에 필요한 패키지들을 requirements.txt 로 관리하여 한 번에 설치할 수 있음

> 이름을 꼭 requirements.txt 로 할 필요는 없는데
>
> 대부분 플젝에서 저 이름으로 관리하니 왠만하면 맞추자

1. ##### requirements.txt 생성

   ```shell
   $ pip freeze > requirements.txt
   ```

   > freeze 는 pip 명령어

2. ##### requirements.txt 예

   ```txt
   alabaster==0.7.12
   alembic==1.0.11
   appnope==0.1.0
   atomicwrites==1.3.0
   attrs==19.1.0
   Babel==2.7.0
   backcall==0.1.0
   ...
   idna==2.8
   imagesize==1.1.0
   importlib-metadata==0.19
   ipykernel==5.1.2
   ipython==7.7.0
   ipython-genutils==0.2.0
   ipywidgets==7.5.1
   itsdangerous==1.1.0
   jdcal==1.4.1
   ```

3. ##### 패키지 설치

   > requirements.txt 가 있는 디렉토리에서 아래 명령어

   ```shell
   $ pip install -r requirements.txt
   ```

4. ##### ref

   - 단순히 해당 버전 이상 설치

     ```tzt
     idna>=2.8
     ```

   - 2 버전대의 아무 버전 설치

     ```txt
     idna>=2.*
     ```

   - 패키지는 venv 에 설치하자 ~

     - [venv 설치하기](../python_virtual_environment)

