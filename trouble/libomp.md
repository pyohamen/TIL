# macOS 에서 XGBoost, LightGBM 라이브러리 안 됨

​	pip install 을 해놓았는데, 라이브러리가 실행되지 않은 것은 처음이였다. 패키지를 설치하고 명령어를 실행했는데

```shell
Traceback (most recent call last):
  File "", line 1, in 
  File "/Users/fakenerd/.envs/env-with-lightgbm/lib/python3.6/site-packages/lightgbm/__init__.py", line 8, in 
    from .basic import Booster, Dataset
  File "/Users/fakenerd/.envs/env-with-lightgbm/lib/python3.6/site-packages/lightgbm/basic.py", line 32, in 
    _LIB = _load_lib()
  File "/Users/fakenerd/.envs/env-with-lightgbm/lib/python3.6/site-packages/lightgbm/basic.py", line 27, in _load_lib
    lib = ctypes.cdll.LoadLibrary(lib_path[0])
  File "/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/ctypes/__init__.py", line 426, in LoadLibrary
    return self._dlltype(name)
  File "/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/ctypes/__init__.py", line 348, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: dlopen(/Users/()/.envs/env-with-lightgbm/lib/python3.6/site-packages/lightgbm/lib_lightgbm.so, 6): Library not loaded: /usr/local/opt/gcc/lib/gcc/7/libgomp.1.dylib
  Referenced from: /Users/()/.envs/env-with-lightgbm/lib/python3.6/site-packages/lightgbm/lib_lightgbm.so
  Reason: image not found
```

일단 OSError 란걸 알았다. 순간 라이브러리가 microsoft 의 것이란게 생각나면서, 초반에 라이브러리가 실행 안 된게 처음이라는 당혹감은 없어지고, 일어날 일이 일어났다고 생각이 들면서 침착해졌다.



# gcc version trouble

​	내 MacOS 의 gcc version 은 8 이지만, 라이브러리의 gcc 컴파일러 버젼이 7이라는 closed issue 를 찾을 수 있었다. [MS/LightGBM issue#1369](https://github.com/microsoft/LightGBM/issues/1369) 

​	MS 에서 처음에 제시한건 라이브러리를 지우고, git 레포지토리에서 clone 해서 직접 라이브러리 설치하고 cmake 하고 디렉토리 새로 설정하고 어쩌구 저쩌구;; 

​	그렇지만 지금은 오픈소스의 시대. Issue comment 맨 밑에 즈음 구원같은 한 문장

```shell
$ brew install libomp
```

​	실제로 brew 로 libomp 패키지 설치하자마자 모든 라이브러리가 정상적으로 loaded 되었다;;



# 교훈

​	더 쉬운 방법이 있다... 늘...

