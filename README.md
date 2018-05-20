# drone-practice
Golang製のCIツール「[Drone(https://github.com/drone/drone)」のトレーニング用リポジトリ

# Drone
DroneはGitリポジトリのPRやtagのプッシュなどのイベントをフックしDockerコンテナ内でジョブを実行することに特化したCIツールである。
リポジトリのルートディレクトリにある`.drone.yml`に従ってpipelineを実行する。  
pipelineは順に実行されるステップから構成される。ステップ毎にDockerコンテナが作成され、コンテナのエントリポイントとして処理が実行される。
ボリュームを共有することによって、前のステップでの生成物を以降のステップで使うこともできる。

## 使い方
各種環境変数を設定する
```
export DRONE_HOST=<構築するDroneのURL>
export DRONE_GITHUB_CLIENT=<Client ID>
export DRONE_GITHUB_SECRET=<Client Secret>
export DRONE_SECRET=<任意の文字列>
```
※ GitHubのOAuth ApplicationとしてDroneを登録し、`Client ID`と`Client Secret`を発行する必要がある。

ローカル環境でテストしたい場合はngrokを使用して、ローカル環境を外部に公開してやると良い（[参考](https://qiita.com/kitaro729/items/44214f9f81d3ebda58bd)）
```
./ngrok http 8080
```

# 参考
- [公式ドキュメント](http://docs.drone.io/installation/)
- [Jenkinsに代わるGo製OSS CIツールDrone](https://engineering.linecorp.com/ja/blog/detail/218)
- [ngrokを使用してローカル環境を外部に公開する](https://qiita.com/kitaro729/items/44214f9f81d3ebda58bd)
