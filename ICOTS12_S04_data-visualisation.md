# 【ICOTS12参加記】ChatGPTがR初心者に勝つ日——Data Visualisation(Main Topic 5)

**Data Visualisation**
2026年7月14日 14:00–15:30 / Plaza P7(South Bank, Brisbane)/ Track: Main Topic 5

初日午後、Main Topic 5「Data Visualisation」を聴講した。2件の発表で構成され、1件目は教員養成カリキュラムの話、2件目はR/ggplot2を競技ゲーム化して教える"ggplot battles"の話。今回は圧倒的に2件目が面白かったので、そちらを中心にまとめる(参考資料として現地で作った ggplot battles の入門ガイド & ゼミ演習プランを [GitHubにアップ済み](https://github.com/kupotti-coder/icots12/blob/main/ggplot_battles_guide.md) なので、あわせて参照)。

## 14:00–14:30 Design and Implementation of Teacher Education Curricula: Preparing Secondary Teachers to Teach Statistics and Data Science

- Gemma Mojica, Hollylynne Lee, Adrian Kuhlman(NC State University, USA)
- Stephanie Casey(Eastern Michigan University, USA)
- Rick Hudson(University of Southern Indiana, USA)

米国NSF助成の "ESTEEM"(Enhancing Statistics Education with E-Modules)プロジェクトの紹介。中高の数学教員志望者向けに、統計・データサイエンスの指導法を学ぶオンライン教材を10年にわたり開発しており、2016年開始のESTEEM Iに続き、現行のESTEEM IIでは "Data Investigation Process"(データを取得・探索・モデル化・分析し、結果を伝えて行動につなげる、という一連のプロセス)を軸に据えている。教材はFoundations(基礎)、Teaching Statistical Association(統計的関連の指導)、Teaching Inferential Reasoning(推測的推論の指導)という3つのモジュール群と、2種類のパフォーマンス評価(スクリーンキャストで自分の分析プロセスを実況説明する課題、タスク設計課題)から構成される。CODAP(無料のWebベースデータ分析ツール)を使った多変量データの調査を軸に、実際の教室映像や生徒の思考過程を見せる"Representations of Practice"、Five Practices(生徒の発言をどう選び・順序立てて全体討論に導くか)などの教員教育フレームワークを組み込んでいる点が特徴的だった。実演として、ジェットコースターのデータをCODAPで調査する6年生の授業映像(生徒同士が「速度が速いほど落差も大きいのか」を自分たちで検証していく様子)が紹介された。教材はCanvas Commons等からダウンロード可能で、Creative Commonsライセンスで公開されている。

## 14:30–15:00 Gamifying Data Visualisation: Teaching ggplot2 Through Competitive Code Golf

- Michael Lydeamore(Monash University, Clayton, VIC, Australia)

こちらが今回一番面白かった発表。モナシュ大学のビジネス統計学の授業では、入学2週間以内にデータを扱わせる「データファースト」の方針を取っており、学生はすぐにコードを書き、雑然としたデータを扱い始める。しかしLydeamore氏いわく、データ可視化は単なる構文(syntax)の問題ではなく、「完成形がどう見えるべきか」というイメージを持ち、そこから逆算してコードに落とし込む反復的な営みである。ところが実際の授業では、白紙の状態から「さあ、グラフを描いてみよう」と言われると、学生は何から手をつければいいか分からなくなる、という悩みを氏は抱えていた。

そこで氏が作ったのが **ggplot battles**(ggplotbattles.dev)というブラウザ完結型のゲームである。CSSの模写対戦ゲーム "CSSBattle" にヒントを得たもので、仕組みは単純明快。

- 完成済みのターゲットとなるggplot2のグラフ画像が提示される
- 学生はブラウザ上のエディタでRのコードを書き、そのグラフをできるだけ忠実に再現する
- 提出すると、ターゲットとの**類似度スコア**が即座に計算・表示される
- WebR(WebAssembly版のR)で動いているため、**RやRStudioのインストールが一切不要**——ブラウザだけで完結する

紹介されたスライド "A battle is just a file" が象徴的で、1つの「バトル」課題はYAMLヘッダー(タイトル・データセット名・使用する色・説明文)とそれに続くごく短いggplot2コードだけで構成される、非常に軽量な仕組みになっている。つまり教員側も新しい課題を簡単に自作でき、実際にGitHubリポジトリ(MikeLydeamore/ggplot2-battles)でコントリビュートを受け付けている。

### 「これは本当に効果があるのか」を検証した実験

単に面白いツールを作った、という話に留まらず、Lydeamore氏はきちんと教育効果を実証する実験まで行っていた点も好感が持てた。スライド "Experimental structure" によれば、チュートリアルのグループを2つに分け、一方には ggplotbattles を使った演習、もう一方には従来型の演習を割り当て(2つの課題の間でどちらを先にやるかは交互に入れ替え)、演習前後にそれぞれpre-quiz・post-quizを実施。スコアを0〜1に正規化し、"post minus pre"(得点の伸び)を効果の指標として比較するという、きちんとした比較対照デザインである。

### 会場を沸かせたリーダーボード

会場で最も盛り上がったのは、実際に表示された **Leaderboard(得点ランキング)** のスクリーンショットだった。

| Name | Score |
|---|---|
| ChatGPT | 100.00% |
| Hollylynne | 87.28% |
| Dean | 87.25% |
| fontika.R | 85.04% |
| The Empty Plot | 12.88% |
| one lazy participant | 12.88% |

なんと、この場でChatGPTに解かせてみたところ**満点(100%)** を叩き出し、会場の統計教育の専門家たちの87%前後を上回ってしまった、という一幕があった。ChatGPTがR初心者どころか経験豊富な統計教育者すら上回ってしまうというデモは、「AIはこの手の"お手本の再現"タスクは既に得意である」という現実を、笑いとともに突きつける瞬間でもあった。

質疑では、この会場に来ている多くの統計教育者にとって、ggplot battlesが「学生のモチベーションを高める入口」として非常に実践的だという評価が多かった一方、上記のChatGPTの結果が示すように、「単純な模写であればAIに任せられてしまう」ことを踏まえて、今後どう課題設計を発展させるかという論点も示唆されていた。

## まとめ

1件目は教員養成という川上での「しっかりしたフレームワークに基づく教材設計」、2件目は大学の教室での「ゲーム化による動機づけ」という対照的なアプローチだったが、どちらも根底には「学生(教員志望者)が実際に手を動かしてデータと向き合う」ことを重視する姿勢が共通していた。特にggplot battlesは、ツールとしての手軽さ・実験による効果検証・そして「ChatGPTが人間の専門家を上回る」という象徴的な一幕まで揃った、非常に見応えのある発表だった。

---
