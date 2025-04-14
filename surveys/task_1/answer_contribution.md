### 共有視野保証と確率的制御バリア関数による分散制御の新規提案

本研究は、マルチエージェントシステムにおける共通視野(CoFoV)保証を、エージェントの位置と姿勢を同時に扱うSE(3)空間上で実現する点に大きな新規性を有する。従来研究は、主に平面上の(SE(2))あるいは単眼視野の問題に限定されており、3次元の複雑なダイナミクス下での共有視野保証には十分な検討がなされていなかった [Panagou+, ICRA2012] [Piasco+, ICRA2016]。

#### 1. SE(3)における共有視野保証  
従来のステレオ視やリーダ–フォロワ形式による視野制御は、ロボット間の相対配置を幾何学的に制約するに留まっており、3次元空間におけるエージェント全体の姿勢・位置を統合的に制御する枠組みは確立されていなかった [Dias+, AAMAS2016]。本手法は、各エージェントのカメラ視野を安全領域として定義し、共有視野の維持を制御不変集合として扱うことで、常時全員が同一の対象を観測可能とすることを実現する。

#### 2. 特徴点に基づく確率的可視性制約とCBFの適用  
従来の視野維持手法は、対象が視野内にあるか否かを決定論的に評価するに留まっていたが、センサの観測不確実性を十分に取り入れていなかった [Panagou+, ICRA2012]。一方、近年は検出確率や信念空間を考慮した計画手法が報告されている [Gao+, ACC2024]。本研究では、各エージェントが観測する特徴点に基づき、その可視性を確率的に評価した上で、制御バリア関数(CBF)に組み込み、常時高い確率で共有視野が確保されるよう制御入力を設計する。これにより、センサノイズ等による不確実性下でも安全な視野維持が可能となる。

#### 3. 非ホロノミックなドローンダイナミクスへの対応と分散最適化  
従来の多くの視野制約付き制御手法は、単純な動力学モデル(例：Dubins車両やクアッドロータの水平姿勢維持)に基づいており、非ホロノミックなダイナミクスを明示的に考慮していなかった [Dias+, AAMAS2016] [Hoang+, ACC2017]。本研究では、機体の並進および回転運動を同時に考慮するSE(3)上の非ホロノミックドローンモデルに対して、高次制約も扱える制御バリア関数(HOCBF)を導入し、各エージェントが局所的な情報交換を通じて分散最適化アルゴリズム(PDMM等)により制御解を求める枠組みを提案する [Lv+, Drones2024] [Zhang+, arXiv2017]。これにより、リアルタイム性とスケーラビリティの両立を実現している。

以上のように，本手法はSE(3)上での共有視野保証、観測特徴に基づく確率的視野評価、および非ホロノミックドローンへの適用と分散最適化という各側面において、従来手法では未踏であった新規性と実用性を有する。

---

### 参考文献 (References)

- Ames, A. D., Xu, X., Grizzle, J. W., & Tabuada, P. (2017). **Control barrier function based quadratic programs for safety critical systems**. *IEEE Transactions on Automatic Control*, 62(8), 3861–3876.  
- Dias, D., Lima, P. U., & Martinoli, A. (2016). **Distributed Formation Control of Quadrotors under Limited Sensor Field of View**. *Proc. of AAMAS 2016*, 1087–1095.  
- Gao, H., Wu, P., Su, Y., Zhou, K., Ma, J., & Liu, C. (2024). **Probabilistic Visibility-Aware Trajectory Planning for Target Tracking in Cluttered Environments**. *Proc. of American Control Conference (ACC 2024)*, (to appear).  
- Hoang, T., Bayasgalan, E., Wang, Z., Tsechpenakis, G., & Panagou, D. (2017). **Vision-based target tracking and autonomous landing of a quadrotor on a ground vehicle**. *Proc. of ACC 2017*, 5580–5585.  
- Koga, S., Zhou, M., Panagou, D., & Atanasov, N. (2023). **Hide and Seek with Visibility Constraints using Control Barrier Functions**. *Proc. of IROS 2023 Workshop on International Pursuit-Evasion*, 1–5.  
- Li, X., Tan, Y., Mareels, I., & Chen, X. (2018). **Compatible Formation Set for UAVs with Visual Sensing Constraint**. *Proc. of ACC 2018*, 6175–6181.  
- Lv, X., Peng, C., & Ma, J. (2024). **Control Barrier Function-Based Collision Avoidance Guidance Strategy for Multi-Fixed-Wing UAV Pursuit-Evasion Environment**. *Drones*, 8(8), 415.  
- Panagou, D., & Kumar, V. (2012). **Maintaining visibility for leader–follower formations in obstacle environments**. *Proc. of ICRA 2012*, 1811–1816.  
- Piasco, N., Marzat, J., & Sanfourche, M. (2016). **Collaborative localization and formation flying using distributed stereo-vision**. *Proc. of ICRA 2016*, 1202–1207.  
- Trimarchi, B., Schiano, F., & Tron, R. (2025). **A Control Barrier Function Candidate for Quadrotors with Limited Field of View**. *arXiv:2410.01277 [eess.SY]*.  
- Zhang, G., & Heusdens, R. (2017). **Distributed Optimization Using the Primal-Dual Method of Multipliers (PDMM)**. *arXiv:1702.00841 [cs.DC]*.