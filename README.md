# t14re-data-capture
t14re-data-captureは，エスタカヤ電子工業株式会社から提供されているミリ波レーダモジュール評価キット TITAN の一種である T14RE シリーズを，python環境で動かすためのプロジェクトです．

python用のプログラムは，評価キット購入時に提供されていますが，本プロジェクトはその利便性を高めるために作成しました．

## 注意事項
以下の点を承知の上，ご利用ください．
- 利用には，評価キットおよび添付された動作設定ファイル（.cfg）が必要です．
- 本プロジェクトはエスタカヤ電子工業（株）と無関係です．本プロジェクトに関するエスタカヤ電子工業（株）への問い合わせは控えてください．
- 評価キットに添付されたマニュアルに従い，技適（技術基準適合証明）に反する使用方法はしないでください．

## できること

### キャプチャ
2種類のモードがあります．
- 指定したファイル数だけキャプチャ
- ユーザから入力を受け付けるまでキャプチャ

### matファイルへの変換
バイナリファイルをmatファイルへ変換することができます．

matファイルを利用することで，MATLABで解析できるようになります．

## 環境構築
1. `build_jupyter_env\t14re.yaml` を`C:\Users\[ユーザー名]\` に置き，Anaconda Prompt を立ち上げます．

2. 以下のコマンドで，仮想環境 `t14re` を作成します．
```
conda env create -f t14re.yaml
```

3. 次に，Jupyter notebook 上で仮想環境を切り替えられるようにします（既に切り替えられるようになっている場合はスキップ）．同じく Anaconda Prompt で以下を実行します．
```
conda activate base
pip install jupyter environment_kernels
jupyter notebook --generate-config
```

作成された`jupyter_notebook_config.py`を vscode などのエディタで開き，以下を追記します．
```
c.NotebookApp.kernel_spec_manager_class='environment_kernels.EnvironmentKernelSpecManager'
c.EnvironmentKernelSpecManager.conda_env_dirs=['C:/Users/[ユーザー名]/.conda/envs/']
```
ただし，`[ユーザー名]`は自身のものに変更してください．追記する場所はどこでも構いません．

4. Jupyter Notebook を立ち上げ，`main_t14re.ipynb` を開き，`Kernel > Change kernel > Environment (conda_t14re)` に切り替えます．正常に切り替われば環境構築は完了です．

## 参考サイト
[エスタカヤ電子工業（株） レーダーモジュール](https://www.s-takaya.co.jp/product/radar/)

[丸文（株） ミリ波レーダモジュール評価キット TITANのご紹介](https://www.marubun.co.jp/technicalsquare/9141/)

[【Anaconda3】指定した仮想環境でJupyter Notebookを動かす](https://www.servernote.net/article.cgi?id=anaconda-jupyter-notebook-on-myenv)
