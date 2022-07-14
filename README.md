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
## フォルダ構成
```bash
├ testlib/
│       ├ example.cp37-win_amd64.pyd(Windows 10用)
│       └ example.cpython-38-x86_64-linux-gnu.so(Ubuntu 20.04用)
├ CALL_example.py
├ some_people.mp4
└ 顔無し区間を含んだテスト動画.mp4
```

## CALL_example.py
`$ python example(arg1, arg2, arg3)`
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