> 구글 클라우드 주피터 노트북 with free GPU

# What is Colab ?

- Colaboratory is a free Jupyter notebook environment that requires no setup and runs entirely in the cloud
- Free GPU support
- Github Friendly
- Easy Collaboration



# How to upload files ?

내가 택한 flow 는

1. 모든 쥬피터파일과 data 는 Github 에 저장

2. 쥬피터파일을 코렙으로 불러옴

   > ~~깃헙에서 쥬피터파일 열고 path 복사: https://**github.com/**pyohamen/data-analysis/blob/master/chapter5/01-used-phone-price-prediction.ipynb~~
   >
   > ~~수정: https://**colab.research.google.com/github/**pyohamen/data-analysis/blob/master/chapter5/01-used-phone-price-prediction.ipynb~~
   >
   > [파일] - [노트열기] - [GitHub tab] 에 `github 에서 불러오고자 하는 쥬피터 파일을 연 후 해당의 경로` 를 검색

3. ~~쥬피터파일 텍스트블럭에 `Open in Colab` 버튼 생성~~ 

   > ~~아래 복사~~

   > ```
   > [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](수정주소)
   > ```

   > 깃헙에 저장할 때 `Open in Colab` 만들어줌

4. 저장

   - colab 에서 작업 후: [파일] - [Github 에 사본저장]

     > 저장 시 `Colaboratory 링크 추자` 체크

   - 로컬 쥬피터에서 작업 후: git push

     > colab 에서 github 으로 저장해줬으니, 로컬 작업 전 `git pull` 꼭!

이렇게 하면 Github 에서나, 로컬의 쥬피터에서나 쥬피터파일을 colab 에서 열어볼 수 있다.

이런 flow 를 선택한 이유는 뭐.. Drive 는 용량이 작으니까..

또 머신러닝 쥬피터 노트북은 github 에서 보관하고 싶다 !

- 단점
  - Github 에서 불러와서 작업하는거라 Autosave 가 안 된다 🥲 잊지 말고 [Github 에 사본저장] 해줘야 함



# How to read data ?

## From Github (file < 25MB)

Github 저장소에서 data 파일을 클릭한 후, `Raw` 를 클릭, 링크를 복사

```python
url = '복사한 raw_data_Github 링크'
df = pd.read_csv(url)
```

## From local

```python
from google.colab import files
uploaded = files.upload()
```

위 명령을 치면 파일을 업로드하는 프롬프트가 뜬다.

```python
import io
df = pd.read_csv(io.BytesIO(uploaded['filename.csv']))
```

