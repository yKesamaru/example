# example用ドキュメント
主にWindows 10使用を前提として扱います。
## 実行環境
- Windows 10
  - Python 3.7.7以上
## 環境構築
```python
pip install -U pip
pip install -U setuptools
pip install -U wheel
pip install -r req.txt
```
`venv`を使用される場合は適切にPath設定をお願いします。
Windows用試作版はライブラリの切り分けをしておりませんのでご了承願います。
```python: req.txt
absl-py==1.1.0
altgraph==0.17
attrs==21.4.0
autopep8==1.6.0
bandit==1.7.4
cachetools==4.2.2
certifi==2022.6.15
charset-normalizer==2.1.0
Click==7.0
click-plugins==1.0.2
click-threading==0.4.4
colorama==0.4.5
cycler==0.10.0
Cython==0.29.30
dlib==19.19.99
face-recognition==1.3.0
face-recognition-models==0.3.0
future==0.18.2
gitdb==4.0.9
GitPython==3.1.27
glob2==0.5
idna==3.3
importlib-metadata==4.3.0
kiwisolver==1.3.1
matplotlib==3.4.2
mediapipe==0.8.10.1
mypy==0.961
mypy-extensions==0.4.3
netifaces==0.10.4
numpy==1.16.4
opencv-contrib-python==4.6.0.66
opencv-contrib-python-headless==4.6.0.66
opencv-python==4.5.5.64
pbr==5.9.0
pefile==2021.5.24
Pillow==8.2.0
protobuf==3.20.1
py2exe==0.10.4.0
pyarmor==6.7.2
pycodestyle==2.8.0
pyenv-win==2.64.7.4
pyinstaller==4.3
pyinstaller-hooks-contrib==2021.1
pyparsing==2.4.7
PyQt5==5.15.4
PyQt5-Qt5==5.15.2
PyQt5-sip==12.9.0
PySimpleGUI==4.43.0
python-dateutil==2.8.1
pywin32-ctypes==0.2.0
PyYAML==6.0
requests==2.28.1
six==1.14.0
smmap==5.0.0
stevedore==3.5.0
toml==0.10.2
tomli==2.0.1
typed-ast==1.5.4
typing-extensions==3.10.0.0
UNKNOWN==0.0.0
urllib3==1.26.10
zipp==3.4.1
```
## フォルダ構成
├ testlib/
│       ├ example.cp37-win_amd64.pyd(Windows 10用)
│       └ example.cpython-38-x86_64-linux-gnu.so(Ubuntu 20.04用)
├ CALL_example.py
├ some_people.mp4
└ 顔無し区間を含んだテスト動画.mp4

## CALL_example.py
`$ example(arg1, arg2, arg3)`
### 引数
- arg1: str
  - DEBUG
    - GUI画面表示
      - `q`押下で終了
    - stdout出力
    - example.log出力
  - INFO
    - example.log出力
- arg2: str
  - INPUT
    - user, passwdがあるならばここで渡す
      - soファイル(Windowsではpyd)内に記述スペースあり
- arg3: int
  - リサイズ後の横幅

```python: CALL_example.py
from testlib.example import example

example("DEBUG", "some_people.mp4", 750)
# example("DEBUG", "0", 750)  # USB CAM 未実装
# example("DEBUG", "顔無し区間を含んだテスト動画.mp4", 750)
# example("DEBUG", "http://219.102.239.58/cgi-bin/camera?resolution=1280", 1200)  # test用
```