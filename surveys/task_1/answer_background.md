## 1. 共有視野保証とCBFに関する研究概要

**背景と意義**  
マルチロボットシステムでは，各ロボットがセンサ情報や視界を共有することにより，監視・捜索・協調輸送などのタスクを効率的に遂行できることが知られている．特にカメラを用いた視覚協調の場合，各ロボットの**共有視野（Common Field-of-View, CoFoV）**が不可欠であり，たとえば複数ドローンが異なる角度から同一対象を観測できることや，通信の見通し線（LOS）維持が求められる [Panagou+, IEEE Trans. Control Netw Syst.2017]．しかし，ロボットは視野角が限られているため，視界共有を保証するための制御技術の開発が急務である．

**制御バリア関数（CBF）の基礎と応用**  
安全なシステム運用のために，CBFはある安全集合（例：視野内に対象が存在する状態）を前方不変に保つための理論的枠組みを提供する．適切なスカラー関数 \( h(x) \) を定義し，\( h(x) \ge 0 \) を安全条件とすることで，各時刻において安全を保証する制御入力を選択できる [Ames+, ECC2019]．この手法は自動運転，ロボット群制御，障害物回避など多くの応用例が示され，複数の安全条件の統合に有利であると報告されている [Yang+, RSS2024]．また，高次制御バリア関数（HOCBF）の導入により，SE(3)空間上の非ホロノミック系に対しても視野制約を厳密に扱うことが可能となっている [Sabattini+, Med. Conf. Control Autom.2013]．

**既存の視野保証手法と分散実装の課題**  
従来はポテンシャル場やMPCを用いた手法が提案され，局所的な視界制約下での隊列制御やセンサグラフの連結性維持に取り組まれてきた．一方で，CBFを用いた手法は，制約違反を防ぎながらリアルタイムに最適な制御入力を計算できるため，有力な候補となる [Capelli+, ICRA2020]．しかし，多数のロボットを対象とする場合，中央集権的な制御は通信負荷や計算量の面で現実的ではなく，各エージェントが局所的に計算し，限定的な通信で連携する分散アルゴリズムの設計が必要である．最近は，補助変数の導入や反復的最適化手法による分散QP解法が検討されており，安全性と分散実装の両立に向けた研究が進められている [Tan & Dimarogonas+, IEEE Control Syst. Lett.2022]．

---

## 2. マルチエージェントVSLAMに関する文献サーベイ

**画像特徴量と自己位置推定**  
マルチエージェントVSLAMでは，各エージェントが撮影した画像から抽出される局所特徴に基づき自己局在を行い，エージェント間で特徴マッチングにより相対位置を推定する．従来のORBやSIFTに代わり，**SuperPoint**のような学習型局所特徴検出・記述器 [DeTone+, CVPR Workshops2018] や，**NetVLAD**によるグローバル記述子 [Arandjelović+, CVPR2016] が高いロバスト性を示し，ループ検出やキーフレームマッチングに貢献している．これらの技術は，マルチエージェント間の地図統合とループ閉じの精度向上に直結する。

**視野重複の重要性**  
画像特徴量のマッチングを成功させるためには，各エージェントが共通のランドマークを観測できるよう，カメラの視野錐台の幾何学的重複が必要である．視野重複が存在すれば，エージェント間でのループ検出が可能となり，その結果として各ロボットの地図統合が実現される [Zhang+, Robotics and Automation Letters2022]．しかし，現状の協調SLAMは，キーフレームの受動的な共有と画像類似度評価に依存しており，視野重複が偶発的に発生しなければマップ統合が成立しないリスクがある。

**アクティブパーセプション：CBFによる視野保証の試み**  
この問題に対して，近年ではロボットの運動制御に視野保持の制約を組み込み，常にあるいは定期的にカメラが共通領域を撮像するよう制御するアプローチが提案され始めている．具体的には，CBFを用いて「他エージェントまたは環境ランドマークを視界に捉える」という安全制約を実現することで，受動的手法の限界を克服しようとする試みである [Trimarchi+, arXiv2025]．また，SLAMの推定とロボットの経路計画を統合することで，視野重複の確保と地図精度の向上を同時に実現する新たな統合最適化枠組みの構築が将来的な展望として期待される。

---

## 結論

本調査では，ロボット群における共有視野保証という課題に対し，CBFを中心とする安全制約付き制御の理論的背景と実装手法，およびこれをマルチエージェントVSLAMに応用する可能性について整理した．各エージェントが限られた視野内で常に共通観測を維持し，分散制御アルゴリズムにより安全かつ効率的に協調動作するための手法は，今後の実機適用およびSLAM最適化との統合に向けた重要な研究課題である．

---

## 参考文献

1. D. Panagou, D. M. Stipanović, and P. G. Voulgaris, “Distributed dynamic coverage and avoidance control under anisotropic sensing,” *IEEE Trans. Control Netw. Syst.*, vol. 4, no. 4, pp. 850–862, 2017.  
2. L. Sabattini, C. Secchi, and N. Chopra, “Decentralized control for the maintenance of strong connectivity for directed graphs,” in *Proc. 21st Mediterranean Conf. Control Autom.*, pp. 978–986, 2013.  
3. B. Capelli and L. Sabattini, “Connectivity maintenance: Global and optimized approach through control barrier functions,” in *Proc. IEEE Int. Conf. Robotics Autom. (ICRA)*, pp. 5590–5596, 2020.  
4. B. Capelli *et al.*, “Decentralized connectivity maintenance with time delays using control barrier functions,” in *Proc. IEEE Int. Conf. Robotics Autom. (ICRA)*, pp. 1586–1592, 2021.  
5. M. M. Asadi and A. G. Aghdam, “Potential-based flocking in multi-agent systems with limited angular fields of view,” in *Proc. American Control Conf. (ACC)*, pp. 299–304, 2014.  
6. D. De Paola, R. De Asmundis, A. Gasparri, and A. Rizzo, “Decentralized topology control for robotic networks with limited field of view sensors,” in *Proc. American Control Conf. (ACC)*, pp. 3167–3172, 2012.  
7. H. A. Poonawala and M. W. Spong, “On maintaining visibility in multi-robot networks with limited field-of-view sensors,” in *Proc. American Control Conf. (ACC)*, pp. 4983–4988, 2017.  
8. M. Santilli, P. Mukherjee, R. K. Williams, and A. Gasparri, “Multirobot field of view control with adaptive decentralization,” *IEEE Trans. Robotics*, vol. 38, no. 4, pp. 2131–2150, 2022.  
9. T. Endo, R. Maeda, and F. Matsuno, “Stability analysis for heterogeneous swarm robots with limited field of view,” in *Proc. Int. Conf. Developments in eSystems Engineering (DeSE)*, pp. 200–205, 2019.  
10. A. D. Ames *et al.*, “Control barrier functions: Theory and applications,” in *Proc. Eur. Control Conf. (ECC)*, pp. 3420–3431, 2019.  
11. P. Glotfelter, J. Cortés, and M. Egerstedt, “Nonsmooth barrier functions with applications to multi-robot systems,” *IEEE Control Syst. Lett.*, vol. 1, no. 2, pp. 310–315, 2017.  
12. Y. Wang, A. D. Ames, and M. Egerstedt, “Safety barrier certificates for collisions-free multi-robot systems,” *IEEE Trans. Robotics*, vol. 33, no. 3, pp. 641–652, 2017.  
13. X. Tan and D. V. Dimarogonas, “Distributed implementation of control barrier functions for multi-agent systems,” *IEEE Control Syst. Lett.*, vol. 6, pp. 1879–1884, 2022.  
14. H. J. LeBlanc *et al.*, “Resilient asymptotic consensus in robust networks,” *IEEE J. Selected Areas Commun.*, vol. 31, no. 4, pp. 766–781, 2013.  
15. H. Lee and D. Panagou, “Maintaining strong \(r\)-robustness in reconfigurable multi-robot networks using control barrier functions,” in *Proc. IEEE Int. Conf. Robotics Autom. (ICRA)*, 2025, (to appear), arXiv:2409.14675.  
16. Y. Yang *et al.*, “Decentralized multi-robot line-of-sight connectivity maintenance under uncertainty,” in *Robotics: Science and Systems (RSS)*, 2024.  
17. B. Trimarchi, F. Schiano, and R. Tron, “A Control Barrier Function Candidate for Quadrotors with Limited Field of View,” in *Proc. IEEE Conf. Decision Control (CDC)*, 2024, arXiv:2410.01277.  
18. T. Fujinami *et al.*, “A Control Barrier Function Approach for Observer-based Visually Safe Pursuit Control with Spherical Obstacles,” *IFAC-PapersOnLine*, vol. 56, no. 12, pp. 340–345, 2023.  
19. F. Bertoncelli *et al.*, “Directed graph topology preservation in multi-robot systems with limited field of view using control barrier functions,” *IEEE Access*, 2023 (under review).
