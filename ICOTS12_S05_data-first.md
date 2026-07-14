# 【ICOTS12参加記】「雑然としたデータ」をどう教育に活かすか——Data First(Main Topic 5)

**Data First**
2026年7月14日 16:00–17:30 / Auditorium(South Bank, Brisbane)/ Track: Main Topic 5

初日午後、Main Topic 5の枠で行われたセッション「Data First」。教員養成・初等中等教育・大学教育という3つの異なるステージを対象に、「きれいに整えられたデータ」ではなく「現実の雑然とした(messy)データ」を教育にどう取り込むかを論じる3件の発表で構成されていた。

## 16:00–16:30 Exploring Messy Data in Teacher Education Using the EDUCATE Framework

- Aisling Leavy(Mary Immaculate College, Limerick, Ireland)
- Sibel Kazak(Middle East Technical University, Türkiye)
- Luca Jotzo(Paderborn University, Germany)
- Susanne Podworny(Paderborn University, Germany)

EU の Erasmus+ プロジェクト「DataSETUP(Promoting Data Science Education for Teacher Education at the University Level)」の一環として行われた研究。ドイツ(10名)とトルコ(13名)の中等数学科の教員志望学生(preservice teachers)を対象に、"EDUCATE" フレームワーク——Get and explore the data(データを取得・探索する)、Formulate the problem(問題を定式化する)、Model/Analyze the data(モデル化・分析する)、Communicate results and engage in an action plan(結果を伝え、行動計画に結びつける)という4つの反復的プロセスと、データ準備・探索的分析・可視化・計算論的思考・倫理的省察・協働という横断的な実践から構成される——に沿って、messyな二次データにどう向き合うかを検証した。

教材として使われたのは、Kaggle上で公開されているメンタルヘルスに関する調査データ(2014年、OSMIによるテック業界従事者向け調査、1,259件・26変数)。性別変数だけで47通りもの表記ゆれがあったり、年齢変数に "99999999999" や "-1726" といった明らかにあり得ない値が含まれていたりする、まさに「汚い」実データである。学生たちはCODAP上でこのデータをクリーニング・分析し、最終的にグループごとに調査質問・分析・結論・限界/倫理的懸念・新たな研究課題をまとめたレポートを提出した。

12グループから提出された19件の統計的調査質問を分析した結果、「関連(association)」を問う質問が最も多く(52.6%)、次いで「比較(comparison)」(42.1%)、「記述(descriptive)」はわずか1件だった。Arnold(2013)の質問の質の基準に照らすと、「意図が明確か」「データで答えられるか」「調べる価値があるか」はほぼ全グループが満たしていた一方、「対象母集団・グループが明確か」を満たしたのは58%にとどまった。分析はほぼ全グループが二方向ドットプロット(two-way dot plot)を用い、多くが列・行・セルパーセンテージなどの数値要約も併用。結論は概ね調査質問と対応づけられており、約半数のグループが「〜と言えるだろう」といった不確実性を含む言い回しを用いていた。データの代表性・サンプリングバイアス・データの陳腐化(2014年のデータであること)への言及も多く見られ、調査後には16件の新たな研究課題(多くが新変数や追加データ収集を要する比較質問)が生まれたという。

## 16:30–17:00 Powerful Big Ideas in Statistics

- Katie Makar(The University of Queensland, Brisbane, Australia)
- Kristen Tripet(University of Canberra, Canberra, Australia)

オーストラリア科学アカデミーの reSolve イニシアチブの一環として開発された、Foundation(4〜6歳)からYear 10(14〜16歳)までの教員研修・授業教材の基盤となる、統計教育における5つの「Powerful Idea(強力な考え方)」を提案する発表。

1. **データは物語る(data tell a story)** — データは単なる数字ではなく文脈を伴うものであり、調査の"middle"(方法論・課題・意思決定のプロセス)にこそ統計的な学びの機会がある。
2. **データは予測の根拠を与える(data provide evidence for predictions)** — 予測は数学的な規則の延長ではなく、不確実性を伴う統計的な営みである。
3. **変動はデータの広がりを説明する(variation describes the spread of data)** — 制御可能な変動要因と不可能な要因を見分けることが、意味のある比較につながる。
4. **分布にはパターンが見える(patterns can be seen in the distribution of data)** — 中心・広がり・形・かたまり・すき間・外れ値など、複数の特徴を組み合わせて分布を読む。
5. **データは表現と文脈を通じて解釈される(data are interpreted through representation and context)** — データの種類によって収集・記録・表現の方法が変わり、その選択自体が「データの物語」の一部になる。

これら5つのアイデアは階層的ではなく相互に連関しており、発達段階に応じて洗練度が上がっていく。論文では reSolve の3つの授業例——Year 1「How far goes my car?」(車のおもちゃを走らせ、素朴な記録と予測を行う)、Year 4「Origami frogs」(折り紙のカエルを飛ばし、ドットプロットとhat plotで分布を捉える)、Year 6「Loopy Aeroplanes」(輪っか付き紙飛行機の設計変数と変動要因を切り分け、比較分布で推論する)——を通じて、同じ5つのアイデアが学年とともにどう深まっていくかを具体的に示していた。

## 17:00–17:30 Learning From Messy Data: The Benefits of Student-Collected Data in the Classroom

- Christian Stratton(Middlebury College, Middlebury, USA)
- Andrew Hoegh(Montana State University, Bozeman, USA)

大学の統計教育において、学生自身が収集した「本物の、雑然とした」データこそが、統計的思考を促す豊かな教室での議論を自然に引き出す、という立場から、3つの実例が紹介される予定。

- 実験計画法の授業における「紙飛行機を使ったランダム化実験」——測定の一貫性やデータラングリング(data wrangling)上の課題が浮き彫りになった例。
- 入門統計学の授業における「反応時間の測定」——外れ値とその統計分析への影響について豊かな議論を生んだ例。
- 学期を通じた「睡眠データの収集プロジェクト」——欠測データ・補完(imputation)・時系列分析における外生変数の利用について議論を促した例。

## まとめ

3件に共通していたのは、「きれいなデータ」ではなく「本物の、雑然としたデータ」を扱わせることの教育的価値である。1件目は教員養成という川上の段階で、教員自身がmessyなデータにどう向き合うかを検証し、2件目は初等・中等教育のカリキュラム設計として「データが物語る・予測の根拠になる」という統計の核となる考え方を提示し、3件目は大学の教室で学生自身にデータを集めさせることの意義を論じる——教育段階は異なるものの、いずれも「データを整形・単純化しすぎない」ことが統計的思考を鍛える、という一貫したメッセージを持つセッションだった。
