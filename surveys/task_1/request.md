# 「一次系システムにおける共有視野を保証するCBF」論文執筆のためのサーベイ要件

## 1. 書き出し・序論のためのサーベイ要件

### 1.1 共有視野保証の背景と重要性
- マルチロボットシステムにおける共有視野(Shared Field of View, CoFoV)の概念と定義
- 共有視野が重要となる応用分野(監視、探索救助、協調作業など)
- 視野制約がマルチロボットシステムの性能に与える影響
- 共有視野保証の技術的課題

### 1.2 制御バリア関数(CBF)の基礎と発展
- CBFの基本概念と安全制約への応用
- CBFを用いた安全保証制御の最近の発展
- 高次CBF(HOCBFs)の理論と応用
- CBFの分散実装に関する研究動向

### 1.3 既存の視野保証手法
- 従来の視野制約付き制御手法(ポテンシャル法、MPC、最適制御など)
- CBFを用いた視野制約の実装例
- 確率的アプローチによる視野保証
- 既存手法の限界と課題

### 1.4 本研究の位置づけと貢献
- 本研究の新規性と技術的貢献
- 一次系システムと二次系システムへの適用
- 分散型実装の利点
- 実用的な応用可能性

## 2. 関連研究のためのサーベイ要件

### 2.1 マルチエージェントシステムにおける視野保証
- 視野制約付きフォーメーション制御
- 視野共有のための協調制御アルゴリズム
- 視野制約下での経路計画
- 視野制約を考慮したコンセンサス問題

以下の論文を調査：
1. Panagou, D., et al. "Multi-objective control for multi-agent systems using Lyapunov-like barrier functions"
2. Sabattini, L., et al. "Vision-based control for multirobot systems"
3. Robuffo Giordano, P., et al. "Bearing-based formation control"
4. Montijano, E., et al. "Vision-based distributed formation control without an external positioning system"

### 2.2 SE(3)上の制御と視野制約
- SE(3)上の剛体運動の制御理論
- 視野制約を考慮したSE(3)上の制御
- 非ホロノミック制約下での視野保証
- SE(3)上の分散制御アルゴリズム

以下の論文を調査：
1. Lee, T., et al. "Geometric tracking control of a quadrotor UAV on SE(3)"
2. Bullo, F., et al. "Geometric control of mechanical systems"
3. Hatanaka, T., et al. "Vision-based cooperative estimation via multi-agent optimization"
4. Spica, R., et al. "Active structure from motion for spherical and cylindrical targets"

### 2.3 制御バリア関数(CBF)の最新動向
- CBFの理論的発展と応用拡大
- 高次CBF(HOCBFs)の設計と安定性解析
- 確率的CBFと不確かさの取り扱い
- CBFと他の制御手法(MPC、最適制御など)の統合

以下の論文を調査：
1. Ames, A.D., et al. "Control barrier function based quadratic programs for safety critical systems"
2. Xiao, W., et al. "Control barrier functions for systems with high relative degree"
3. Lindemann, L., et al. "Control barrier functions for signal temporal logic tasks"
4. Nguyen, Q., et al. "Exponential control barrier functions for enforcing high relative-degree safety-critical constraints"

### 2.4 分散型CBFと最適化手法
- 分散型CBFの設計と実装
- 分散型最適化手法(ADMM、PDMM)とCBFの統合
- マルチエージェントシステムにおける分散型安全制約
- 通信制約下での分散型CBF

以下の論文を調査：
1. Wang, L., et al. "Safety barrier certificates for collisions-free multirobot systems"
2. Borrmann, U., et al. "Control barrier functions for multi-agent systems"
3. Chen, Y., et al. "Decentralized non-communicating multiagent collision avoidance with deep reinforcement learning"
4. Notomista, G., et al. "Constraint-driven coordinated control of multi-robot systems"

### 2.5 二次系システムにおける視野保証
- 二次系ダイナミクスを持つロボットの制御
- 非ホロノミック制約下での視野保証
- 二次系システムにおけるHOCBFの設計
- 二次系システムの分散制御

以下の論文を調査：
1. Nguyen, Q., et al. "Exponential control barrier functions for enforcing high relative-degree safety-critical constraints"
2. Xiao, W., et al. "Control barrier functions for systems with high relative degree"
3. Tan, H., et al. "Barrier functions for multiagent systems with high-order dynamics"
4. Wu, G., et al. "Safety-critical control of dynamic systems with control barrier functions and applications"

## 3. 具体的な調査ポイント

### 3.1 数学的定式化
- 共有視野の数学的定義と表現方法
- 確率的視野モデルの定式化
- CBFとHOCBFの数学的定式化
- 分散型最適化問題の定式化

### 3.2 アルゴリズム設計
- 単一/複数特徴点追従のためのCBF設計
- 複数エージェントの共通特徴点追従のためのCBF設計
- 分散型実装のためのアルゴリズム
- 二次系システムのためのHOCBF設計

### 3.3 性能評価指標
- 共有視野保証の評価指標
- 計算効率の評価方法
- 分散アルゴリズムの収束性評価
- 実用的なシナリオでの性能評価基準

### 3.4 実装と検証
- シミュレーション環境の構築方法
- 実機実験のための要件
- 結果の可視化手法
- 比較手法の選定

## 4. 調査結果の活用方針

1. 序論と関連研究セクションの執筆に直接活用
2. 本研究の新規性と貢献を明確に位置づけるための比較材料として活用
3. 数学的定式化の妥当性検証に活用
4. 性能評価の方法論と比較対象の選定に活用
5. 今後の研究課題の特定に活用

## 5. 調査方法

1. 学術データベース(IEEE Xplore, Google Scholar, ACM Digital Library)での文献検索
2. 主要国際会議(ICRA, IROS, CDC, ACC)の最新プロシーディングスの調査
3. 主要ジャーナル(IEEE Transactions on Robotics, IEEE Transactions on Automatic Control)の最新号の調査
4. 引用ネットワーク分析による関連文献の特定
5. 著名研究者のウェブサイトやプレプリントサーバー(arXiv)の調査
