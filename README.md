# t14re-data-capture
t14re-data-captureは，エスタカヤ電子工業株式会社[1]から提供されているミリ波レーダモジュール評価キット TITAN [2]の一種である T14RE シリーズを，python環境で動かすためのプロジェクトです．

python用のプログラムは，評価キット購入時に提供されていますが，本プロジェクトはその利便性を高めるために作成しました．

## デモ動画
![demo_movie](https://user-images.githubusercontent.com/60993969/208602810-7fcc65c6-7b51-44b9-9126-72a4ba783c6c.gif)

### 使用手順
1. 必要なスクリプトを読み込み，設定ファイル(.cfg)をロード・送信します．

2. PC上でレーダを認識させます．

3. `capture`関数でデータをキャプチャします．引数に0以下の整数を与えると，ユーザから入力を受けるまでキャプチャします．1以上の整数を与えると，そのファイル数だけキャプチャします．取得したデータは同じディレクトリの`data_t14re`フォルダ内に保存され，フォルダ名が取得日時になっています．

4. （任意）`ConvertDataFromBin2Mat`関数でmatファイルへ変換することができます．matファイルはMATLAB上でロードできます．

## 環境構築
1. git cloneコマンドで本リポジトリをローカル環境に複製してください．場所はどこでも構いません．
```
git clone https://github.com/kossyprg/t14re-data-capture.git
```
なお，本リポジトリの内容が更新された場合は，`git pull origin main`で更新できます．

2. `build_jupyter_env\t14re.yaml` を`C:\Users\[ユーザー名]\` に置き，Anaconda Prompt を立ち上げます．

3. 以下のコマンドで，仮想環境 `t14re` を作成します．
```
conda env create -f t14re.yaml
```

![conda_env_create](https://user-images.githubusercontent.com/60993969/208572148-c1d7e7a7-1ff8-4f50-a007-e3cf1284cdfd.gif)



4. 次に，Jupyter notebook 上で仮想環境を切り替えられるようにします[3]（既に切り替えられるようになっている場合はスキップ）．同じく Anaconda Prompt で以下を実行します．
```
conda activate base
pip install jupyter environment_kernels
jupyter notebook --generate-config
```

![jupyter_notebook_generate_config](https://user-images.githubusercontent.com/60993969/208572290-4672566c-9fc5-4ee4-9fba-d6d08caa7464.gif)


作成された`jupyter_notebook_config.py`を vscode などのエディタで開き，以下を追記します．
```
c.NotebookApp.kernel_spec_manager_class='environment_kernels.EnvironmentKernelSpecManager'
c.EnvironmentKernelSpecManager.conda_env_dirs=['C:/Users/[ユーザー名]/.conda/envs/']
```
ただし，`[ユーザー名]`は自身のものに変更してください．追記する場所はどこでも構いません．

![jupyter_notebook_generate_config_edit_v2](https://user-images.githubusercontent.com/60993969/208579877-89124351-2125-45cc-b6ce-50259f919e9d.gif)

5. Jupyter Notebook を立ち上げ，`main_t14re.ipynb` を開き，`Kernel > Change kernel > Environment (conda_t14re)` に切り替えます．正常に切り替われば環境構築は完了です．

![jupyter_notebook_change_kernel](https://user-images.githubusercontent.com/60993969/208572445-60335e40-9ce7-45d1-b3ca-7cb3e4ee8302.gif)

## 注意事項
以下を承知の上，ご利用ください．
- 利用には，評価キットおよび添付された動作設定ファイル（.cfg）が必要です．
- 本プロジェクトはエスタカヤ電子工業（株）と無関係です．本プロジェクトに関するエスタカヤ電子工業（株）への問い合わせは控えてください．
- 評価キットに添付されたマニュアルに従い，技適（技術基準適合証明）に反する使用方法はしないでください．

## 参考サイト
[1] [エスタカヤ電子工業（株） レーダーモジュール](https://www.s-takaya.co.jp/product/radar/)

[2] [丸文（株） ミリ波レーダモジュール評価キット TITANのご紹介](https://www.marubun.co.jp/technicalsquare/9141/)

[3] [【Anaconda3】指定した仮想環境でJupyter Notebookを動かす](https://www.servernote.net/article.cgi?id=anaconda-jupyter-notebook-on-myenv)
