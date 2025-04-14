以下に、各理論要素の内容を論文執筆用に圧縮した文章を示す．リンク表記は全て削除し，引用箇所は識別可能な記法(例：[Ames+, IEEE TAC 2017])を用いて表記している．なお，最後の参考文献リストは原文の通り保存してある．

---

### 制御バリア関数 (Control Barrier Functions, CBF)

CBFは，システム状態がある安全集合内に留まることを保証するためのLyapunov関数に類似した概念である．もともとはバリア関数やバリア証明の枠組みに基づいており，PrajnaやTeeらの初期研究を発展させた形で，Amesらは制御Lyapunov関数(CLF)と統合した安全・安定制御のための二次計画問題(QP)による実装手法を提案した [Ames+, IEEE TAC 2017]．その後，制御入力の摂動やモデリング不確かさに対するロバスト性，初期状態が非ゼロの場合の安全保証，さらに外部入力を含む安全性(ISS)や時間依存の仕様に対応する拡張が進められ，自動運転車やロボットなど安全クリティカルなシステムへの応用が広がっている [Taylor+, 2020]．

---

### 高次制御バリア関数 (High Order Control Barrier Functions, HOCBF)

従来のCBFは制約関数の相対次数が1であることを仮定していたが，多くの実システムでは安全制約が高次微分に依存するため，新たな理論が必要とされた．XiaoとBeltaらは，高次の相対次数に対応する補助関数の連鎖的な構成によりHOCBFを定式化し，最終的にゼロイング条件を課すことで安全集合の不変性を保証する枠組みを確立した [Xiao & Belta, IEEE TAC 2022]．加えて，多数の安全制約や制御入力制限下でQPの実行可能性を担保するために，ペナルティ法やパラメータ化法を導入する手法も提案されている．これにより，自動車の隊列走行や高速ロボット操作といった応用事例で高次の安全制御が実現されている．

---

### プライマル・デュアル乗数法 (PDMM)と不等式制約付き合意問題

PDMMは，分散最適化および合意問題を解くためにADMMを拡張した手法である．Changらは，ネットワーク上の各エージェントが局所目的関数を持ち，隣接エージェント間で等式制約を共有する設定において，エッジ単位での並列更新により高速収束を実現するPDMMを提案した [Chang+, IEEE TSP 2016]．さらに，ZhangとHeusdensは，双対変数に非負制約を課すことで線形不等式制約も取り扱えるよう改良し，非同期更新や通信遅延下での理論的収束性を保証するアルゴリズムを提示している [Zhang & Heusdens, IEEE TSIPN 2024]．

---

### 分散型CBFとマルチエージェント協調制御

分散型CBFは，複数ロボットが局所的な安全制約を各自で実装することで，中央集権的な監督なしに全体の安全性を保証する手法である．たとえば，Wangらは各ロボット間で定義されるバリア関数を用い，衝突回避を実現する安全バリア証明に基づく分散制御器を提案した [Wang+, IEEE Robotics 2017]．また，編隊維持やネットワーク連結性の確保，障害物回避などの他の協調制御タスクにも応用される一方，局所QPの解法における実行可能性やデッドロックの問題に対しては，ペナルティ付きCBFやMARLと統合した手法による解決策が検討されている [Jankovic+, arXiv 2022]．

---

### SE(3)上の剛体運動制御(特にクアッドロータへの応用)

クアッドロータの制御は，6自由度の剛体としての位置・姿勢制御と，限られた入力(全推力と3軸トルク)によるアンダーアクチュエイト性という課題がある．従来のオイラー角や四元数を用いた手法は特異点やアンワインド現象の問題を抱えていたが，LeeらはSE(3)上の回転行列を直接扱う幾何学的制御手法を提案し，グローバル(またはほぼ大域的)な安定性を理論的に示した [Lee et al, CDC 2010]，[Lee et al, Asian J Control 2013]．この手法により，倒立状態からの安定な制御やアグレッシブな機動も実現可能となり，最小スナップ軌道追従やMPCとの融合など，応用範囲がさらに拡大している．

---

### 可視性・視野制約の連続的最適化定式化

ロボットやカメラによる対象追跡・観測では，対象を常に視野内に保持するための非線形・非凸な制約の取り扱いが重要である．基本的には，対象位置とカメラ光軸との角度制約や画像平面上の位置制約が用いられるが，これらを滑らかな関数として定式化し，勾配法や凸緩和を用いる最適化手法が提案されている [Wang+, arXiv 2021]．Bonattiらは映像品質の維持を目的に，視野外への逸脱に対するコストを設計し，一方でZhangとScaramuzzaは候補ヨー角をサンプリングする手法を用いた知覚重視のMPCにより，厳密な視野制約を実現する方法を示している [Zhang & Scaramuzza, ICRA 2018]．このようなアプローチにより，知覚と運動の統合的最適化が進展している．

---

## 参考文献 (References)

- Ames, A. D., Xu, X., Grizzle, J. W., & Tabuada, P. (2017). **Control barrier function based quadratic programs for safety critical systems**. *IEEE Transactions on Automatic Control, 62*(8), 3861–3876.  
- Xiao, W., & Belta, C. (2022). **High-order control barrier functions**. *IEEE Transactions on Automatic Control, 67*(7), 3655–3662.  
- Chang, T.-H., Hong, M., Liao, W.-C., & Wang, X. (2016). **Distributed optimization using the primal-dual method of multipliers**. *IEEE Transactions on Signal Processing, 64*(2), 447–461.  
- Zhang, G., & Heusdens, R. (2024). **Distributed optimisation with linear equality and inequality constraints using PDMM**. *IEEE Transactions on Signal and Information Processing over Networks*. (早期公開)  
- Wang, L., Ames, A. D., & Egerstedt, M. (2017). **Safety barrier certificates for collision-free multi-robot systems**. *IEEE Transactions on Robotics, 33*(3), 661–674.  
- Chen, Y., Singletary, A., & Ames, A. D. (2021). **Guaranteed obstacle avoidance for multi-robot operations with limited actuation: A CBF approach**. *IEEE Control Systems Letters, 5*(1), 127–132.  
- Lee, T., Leok, M., & McClamroch, N. H. (2010). **Geometric tracking control of a quadrotor UAV on SE(3)**. In *Proc. of IEEE Conf. on Decision and Control* (pp. 5420–5425).  
- Lee, T., Leok, M., & McClamroch, N. H. (2013). **Nonlinear robust tracking control of a quadrotor UAV on SE(3)**. *Asian Journal of Control, 15*(2), 391–408.  
- Bonatti, R., Zhang, Y., Choudhury, S., Wang, W., & Scherer, S. (2018). **Autonomous drone cinematographer: Smooth, safe, occlusion-free trajectories for aerial filming**. In *Proc. of ISER 2018* (pp. 119–129).  
- Wang, Q., Gao, Y., Ji, J., Xu, C., & Gao, F. (2021). **Visibility-aware trajectory optimization with application to aerial tracking**. arXiv:2103.06742 [cs.RO].  
- Zhang, Z., & Scaramuzza, D. (2018). **Perception-aware receding horizon navigation for MAVs**. In *Proc. of IEEE Int. Conf. on Robotics and Automation* (pp. 2534–2541).  
