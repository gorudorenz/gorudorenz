
# 👋 こんにちは！ゴールドレンズです！

> Python / Docker / Kubernetes を軸に、エッジAI・リアルタイムWebアプリ・インフラ自動化まで幅広く開発しています。

---

## 🧑‍💻 About Me

- 🔭 バックエンド開発・コンテナ基盤の構築・運用を担当してきました
- 🌱 ラズパイが好きで中学3年生から触ってます！
- 📫 連絡先: gorudorenz@icloud.com
- 🌍 拠点: 千葉県

---

## 🛠️ Tech Stack

### Languages & Frontend
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)

### Backend & Database
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)

### Infrastructure & DevOps
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Raspberry Pi](https://img.shields.io/badge/Raspberry_Pi-A22846?style=for-the-badge&logo=raspberry-pi&logoColor=white)
![Tailscale](https://img.shields.io/badge/Tailscale-242424?style=for-the-badge&logo=tailscale&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)

### AI / LLM
![Ollama](https://img.shields.io/badge/Ollama-000000?style=for-the-badge&logo=ollama&logoColor=white)

### Libraries & Tools
![Leaflet](https://img.shields.io/badge/Leaflet.js-199900?style=for-the-badge&logo=leaflet&logoColor=white)

### IoT / Hardware
![ESP32](https://img.shields.io/badge/ESP32-E7352C?style=for-the-badge&logo=espressif&logoColor=white)
![Home Assistant](https://img.shields.io/badge/Home_Assistant-41BDF5?style=for-the-badge&logo=home-assistant&logoColor=white)
![ESPHome](https://img.shields.io/badge/ESPHome-000000?style=for-the-badge&logo=esphome&logoColor=white)

---

## 🚀 Projects
### 🚃 [JR東日本 リアルタイム列車マップ](https://github.com/yourusername/jr-east-realtime-map)
> 公共交通オープンデータ（ODPT API）を使ったリアルタイム列車位置ビジュアライザー

- **概要**: JR東日本全路線の列車位置を地図上にリアルタイム表示。路線カラーで色分けされた矢印アイコンで進行方向も可視化
- **技術スタック**: JavaScript (Vanilla), Leaflet.js, ODPT API
- **工夫したポイント**:
  - `Promise.all` で駅・路線データを並列取得し初期化を高速化
  - `atan2` による進行方向角度計算でアイコンを列車の向きに動的回転
  - 路線ごとのカラーコードを `DivIcon` に動的反映
  - 30秒ごとの自動更新で常に最新の列車位置を表示
<img width="4284" height="1486" alt="IMG_7115" src="https://github.com/user-attachments/assets/1d42f649-ca86-4fd2-a2e5-f254bfd8e04d" />


---

### 📍 [リアルタイム待ち合わせアプリ](https://github.com/yourusername/meetup-app)
> Firebase Firestoreを使い、複数人がリアルタイムで待ち合わせ場所を共有できるWebアプリ

- **概要**: 地図をタップして待ち合わせ場所を設定すると、URLを共有した全員の画面に即時反映。現在地からの距離・徒歩時間も自動計算
- **技術スタック**: JavaScript (Vanilla), Leaflet.js, Firebase (Firestore + Hosting)
- **工夫したポイント**:
  - Firestore の `onSnapshot` でサーバーレスなリアルタイム同期を実現
  - `geolocation.watchPosition` で自分の現在地を継続追跡
  - URLパラメータ（`?id=`）でルームを分離し複数グループに対応
  - Haversine公式で正確な直線距離と徒歩所要時間を計算
  - Firebase Hosting でデプロイ・公開済み

---

---

### 🤖 [PicoClaw × ローカルLLM エージェント環境](https://github.com/yourusername/picoclaw-llm)
> Raspberry Pi × Mac（Ollama）でAPIコストゼロのエッジAIエージェント基盤を構築

- **概要**: Mac上で動くローカルLLM（Llama 3.1 8B）を「脳」に、Raspberry Pi 5上のロボットアーム（PicoClaw）を「体」として動かす自律型エージェント環境。TailscaleのVPNで2デバイス間をセキュアに接続し、Discord Botをインターフェースとして制御
- **技術スタック**: Python 3.13, Ollama, Llama 3.1 (8B), OpenClaw, Sipeed PicoClaw, Docker / Docker Compose, Tailscale, Raspberry Pi 5
- **工夫したポイント**:
  - OllamaのAPIをOpenAI互換形式として扱い、既存エージェントライブラリを最小改修でローカル環境に適合
  - Tailscaleで `100.x.x.x` 系のIP固定・暗号化通信を確保しクロスデバイス連携を実現
  - リリース直後の Python 3.13 + OpenClaw 2026.2.15 という最新環境をDockerで分離・安定稼働
- **解決した技術的課題**:
  - デフォルト設定で12,000トークン超のシステムプロンプトが送信されLLMがハングする問題 → `hooks.internal.enabled: false` 等で不要プロンプトを徹底排除し高速応答を実現
  - 新バージョンのConfigスキーマ厳格化でコンテナが再起動ループ → `openclaw doctor --fix` でスキーマ検証・修正
  - `docker.sock` 権限不足エラー → dockerグループへのユーザー追加と明示的パス指定で解決

---

### 🌡️ [Home Assistant & ESPHome スマート温湿度計](https://github.com/yourusername/esphome-thermometer)
> ESP32 + DHT11 センサーを自作し、セルフホストの Home Assistant でリアルタイム室温モニタリングを実現

- **概要**: umbrelOS で運用するホームサーバー上の Home Assistant と ESPHome を連携させ、自作 ESP32 デバイスで室温・湿度を60秒間隔で収集・可視化するスマートホーム基盤を構築
- **技術スタック**: ESP32 (NodeMCU), DHT11, ESPHome, Home Assistant, umbrelOS, ESP-IDF v5.5.2
- **工夫したポイント**:
  - YAML でハードウェアの挙動を定義する ESPHome の IaC 的アプローチを採用し、デバイス設定をコードで管理
  - 初回は umbrelOS でビルド → Mac 経由で USB 書き込み、安定後は OTA（Wi-Fi 経由）に切り替えるハイブリッドデプロイを確立
  - `!secret` タグによる機密情報の分離管理で段階的にセキュアな構成へ移行
- **解決した技術的課題**:
  - mDNS 名前解決失敗（`.local` 接続不可）→ ログから割り当てIPを特定し `use_address` で直接指定
  - シリアル書き込みエラー → BOOT ボタンで手動フラッシュモード移行 + センサー配線を外して電力安定化
  - 起動ループ（`flash read err`）→ Web Serial API で Factory Reset 後にバイナリ再ビルド・再書き込みで復旧
  - API 認証エラー → YAML に `api:` セクションを明示追加、Home Assistant 側でエンティティをクリーン再登録

---

### 📊 [Raspberry Pi ネイティブ監視システム](https://github.com/yourusername/rpi-native-monitoring)
> Docker を使わず Prometheus + Node Exporter をバイナリ直接動作させた軽量監視基盤

- **概要**: Umbrel OS (Raspberry Pi 5) 上で Prometheus と Node Exporter をネイティブバイナリとして稼働させ、Grafana でリアルタイム可視化。コンテナのオーバーヘッドを排除し、CPU・メモリ・温度などOSの生メトリクスを直接収集
- **技術スタック**: Prometheus v2.50.0, Node Exporter v1.7.0, Grafana, systemd, Tailscale, Umbrel OS (Debian aarch64)
- **工夫したポイント**:
  - `systemd` ユニットファイルを独自定義（`Restart=always` / `Wants=network-online.target`）し、OS再起動後も自動で監視が復旧する堅牢な構成を確立
  - `--web.listen-address="0.0.0.0:9090"` でマルチインターフェース待機を設定し、LAN・Tailscale VPN・Docker内部ネットワークからの同時アクセスを両立
  - 自宅内はLAN IP、外出先は Tailscale VPN という使い分けによるハイブリッドアクセス設計
- **解決した技術的課題**:
  - `No route to host` → GrafanaコンテナからホストOSへの通信がUmbrel内部ファイアウォールで遮断 → 仮想ゲートウェイ（`10.21.21.1`）でなく物理NIC IP（`192.168.x.x`）経由に変更して経路確保
  - Docker内DNSがTailscaleホスト名を解決できない → ホスト名指定をやめ静的IPで直接指定
  - `prometheus.yml` のインデントミス・重複定義によるパースエラー → `global` とジョブの親子構造を整理して修正

---

### 🗳️ [Discord × Ollama マルチLLM 多数決Bot](https://github.com/yourusername/discord-llm-vote)
> 複数のローカルLLMが互いの意見を再評価しながら全会一致を目指す「合議制AI Bot」

- **概要**: Ollama上で動く複数の軽量LLM（gemma / qwen / deepseek-r1 / tinydolphin）がDiscord上で投票・再審議・全会一致推論を行うシステム。単一モデルの回答ブレを補い、AI同士の合意形成によって信頼性を向上させる実験的AIアーキテクチャ
- **技術スタック**: Python 3, discord.py, asyncio, Ollama, Raspberry Pi 4 (Linux)
- **工夫したポイント**:
  - 単純な多数決に留まらず「少数派意見の再審議」と「全会一致モード」を実装。全モデルが同じ回答に収束するまで他モデルの理由を再考材料として再推論を繰り返す合意形成アルゴリズムを設計
  - `asyncio.create_subprocess_exec()` による非同期LLM呼び出しで、長時間推論中も Discord Gateway の heartbeat を維持しBotのフリーズを解消
  - Raspberry Pi 4 のメモリ制約に対応するため、複数モデルの並列実行から直列実行＋待機時間方式に変更しCPU/メモリ負荷を分散
  - DeepSeek-R 系の内部思考（`Thinking…`）出力を正規表現パーサーで除去し、`Answer:` / `Reason:` のみ抽出する専用パーサーを実装
  - プロンプトエンジニアリングで `both` / `N/A` 等の曖昧回答を禁止し、小型モデルでも yes/no 形式の出力を強制
  - 投票結果を Markdown コードブロックの表形式で整形し、Discord 上でモデルごとの判断・理由を直感的に比較できる UI を実装
- **解決した技術的課題**:
  - `subprocess.run()` の同期実行 → Bot全体がフリーズ → `asyncio.create_subprocess_exec()` に全面移行して安定化
  - 並列モデル実行によるメモリ不足（Raspberry Pi 4）→ 直列処理＋インターバル方式で解消
  - DeepSeek-R の推論ログが投票解析を破壊 → 専用正規表現パーサーで `Answer:` / `Reason:` のみ抽出
<img width="4284" height="5712" alt="IMG_7595" src="https://github.com/user-attachments/assets/e50bf37e-e8c8-43c1-a2df-a9b422699ab1" />

## 📊 GitHub Stats

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=yourusername&show_icons=true&theme=default&hide_border=true)
![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=yourusername&layout=compact&theme=default&hide_border=true)

---

## 📝 現在の関心 / 学習中

- [ ] Go 言語の習得
- [ ] クラウド資格取得（AWS / GCP）

---

## 🤝 Contact

転職・業務委託・勉強会などお気軽にご連絡ください。

---

*Last updated: 2026/05*

<!--
**gorudorenz/gorudorenz** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
