# 【ICOTS12参加記】可視化を「推論」として教える——Dianne Cookのキーノートとtidyverse・knitrへの系譜

## Towards a Richer Statistical Thinking: Teaching Visualisation as a Tool for Inference

**Speaker:** Dianne Cook（Monash University）  
**Type:** Keynote  
**Date:** 2026年7月17日（ICOTS12 Day 4）

Dianne Cookによるキーノートの中心的な主張は、**データ可視化を、記述統計のための補助的な作図ではなく、統計的推論の道具として教えるべきだ**というものである。

従来の統計教育では、探索的データ解析と統計的推論が分離されがちである。前者ではグラフを描いてデータの特徴を探し、後者では検定や信頼区間を使って正式な結論を導く。しかしCookは、この区別は人工的であり、現在では可視化と推論を一体として扱うための理論とソフトウェアが整っていると主張する。

講演では、次の3つの考え方が、可視化を推論として教えるための柱として示された。

1. Grammar of Graphics
2. Visual inference
3. Uncertainty-aware visualisation

## 1. Grammar of Graphics：作図を体系的な分析にする

`ggplot2`で採用されているGrammar of Graphicsでは、グラフを「なんとなく描くもの」ではなく、データ、変数と視覚属性の対応、幾何オブジェクト、統計変換、座標系、ファセットなどの構成要素に分解して考える。

この枠組みによって、可視化は単なる見栄えの調整ではなくなる。どの変数を位置、色、大きさなどに対応させ、何を比較し、どのような構造を表現するのかを明示的に考える、体系的な統計活動となる。

したがって、Grammar of Graphicsを教えることは、単に`ggplot2`の書き方を教えることではない。学生に対して、**グラフを構成する選択の一つ一つが、データに対する問いや仮説と結びついている**ことを理解させることに意味がある。

## 2. Visual inference：グラフで仮説検定を行う

Cookの研究を特徴づける考え方の一つが、visual inference（視覚的推論）である。Rパッケージの`nullabor`では、lineup protocolと呼ばれる方法を使って、グラフを用いた仮説検定を実施できる。

典型的なlineupでは、複数のグラフを並べ、そのうち1枚だけを実データから作り、残りを帰無仮説の下で生成したデータから作る。観察者は、どのグラフが実データなのかを知らされず、他とは異なるパターンを持つグラフを選ぶ。

例えば20枚のグラフのうち1枚だけが実データである場合、帰無仮説の下で偶然正解する確率は1/20、すなわち0.05となる。実データのグラフが識別されれば、観察されたパターンが帰無仮説の下では現れにくいという判断につながる。

重要なのは、lineup protocolが「通常の仮説検定を初心者向けに簡略化した例え」ではない点である。人間の視覚的判断を利用する、正式な統計的推論の方法として構成されている。

この方法は、通常の検定統計量を設定しにくい問題にも適用できる。

- データにクラスターらしい構造があるか
- 外れ値が偶然の変動を超えて目立っているか
- 回帰モデルの残差に構造が残っているか
- ある可視化デザインが、別のデザインよりパターンを見つけやすいか

つまり、グラフは分析結果を説明する最後の道具ではなく、**仮説を検討し、証拠の強さを評価する分析装置**になる。

## 3. Uncertainty-aware visualisation：不確実性をグラフに組み込む

講演の第3の柱は、uncertainty-aware visualisation、すなわち不確実性を意識した可視化である。

通常のグラフでは、観測値や推定値が確定した値であるかのように描かれることが多い。しかし実際には、標本変動、測定誤差、モデルの推定誤差などが含まれている。点推定値だけを強く描くと、確実ではない差やパターンを、実在する特徴として過大に伝えてしまう可能性がある。

`ggdibbler`は、こうした測定された変動をGrammar of Graphicsの中に取り込み、既存の`ggplot2`形式のグラフに不確実性を反映させることを目指すパッケージである。

これは単にエラーバーを追加するという発想にとどまらない。不確実性が大きい場合には、見えているパターンそのものを弱めたり、複数の可能な状態を示したりすることで、学生が「値」と「値の不確かさ」を同時に考えられるようにする。

この考え方によって、学生は次のような問いを持つようになる。

- この差は、推定の不確実性を考えても残るのか
- 見えているパターンは、別の標本でも再現されるのか
- どの部分については強く主張でき、どの部分については慎重であるべきか

## 探索と推論を一つの循環として教える

Cookの提案では、探索的データ解析と統計的推論を、別々の章や授業として切り離さない。

学生はグラフを使ってパターンを発見し、そのパターンが偶然でも生じるかをlineupで検討し、さらに推定の不確実性を考慮して結論の強さを判断する。この過程を行き来することで、探索と推論は一つの循環になる。

従来型の流れは、次のようになりやすい。

> グラフを描く → 特徴を説明する → 後の章で検定を学ぶ

Cookが提案する流れは、次のようになる。

> グラフを描く → パターンを発見する → 帰無仮説の下のグラフと比較する → 不確実性を検討する → 主張を修正する

このように教えれば、学生はグラフを見て自由に感想を述べるだけでも、計算した検定結果を機械的に報告するだけでもなくなる。可視化を使いながら、証拠に基づいて主張の強さを調整する統計的思考を身につけられる。

## 授業・評価への示唆

この考え方を学部・大学院教育に取り入れる場合、課題や評価も変える必要がある。

評価すべきなのは、単に「正しいグラフを作れたか」「きれいな図になっているか」ではない。例えば、次のような統計的判断を評価対象にできる。

- 見つけたパターンについて、適切な帰無仮説を設定できるか
- 帰無仮説の下で、どのようなグラフが現れるかを説明できるか
- lineupから得られる証拠を過大評価せずに解釈できるか
- 不確実性を考慮したときに、結論を適切に修正できるか
- 可視化デザインの違いが、読み手の判断に与える影響を比較できるか

特に興味深いのは、visual inferenceがデータの分析だけでなく、可視化方法自体の評価にも使える点である。二つのグラフデザインのどちらがパターンを発見しやすいかを、観察者の正答率などによって比較できる。可視化を「好み」や「美しさ」だけで評価するのではなく、統計的な検証対象にできる。

## Dianne CookはRの世界でどのような人か

Dianne Cookは、R、とりわけ統計グラフィックス、高次元データの可視化、対話的グラフィックス、visual inferenceの分野で非常に著名な研究者である。

Iowa State Universityで約20年間勤務した後、Monash Universityの統計学教授となった。GGobiの開発者の一人であり、GGobiの高次元可視化機能をR上で発展させた`tourr`をはじめ、`nullabor`、`GGally`、`naniar`、`brolgar`など、多数のRパッケージに関わっている。

また、R Foundationの理事を務め、The R JournalおよびJournal of Computational and Graphical Statisticsの編集にも携わってきた。

一般のR利用者にはHadley Wickhamほど名前が知られていないかもしれない。しかし、現代のRにおける二つの大きな流れ、すなわち

- `ggplot2`・tidyverseを中心とするデータ探索と可視化
- `knitr`・R Markdownを中心とする再現可能なレポーティング

の中心人物を博士課程で指導した研究者でもある。

## Hadley Wickhamとの関係

Hadley Wickhamは、`ggplot2`の開発者であり、`dplyr`、`tidyr`などを含むtidyverseの中心的な設計者として知られている。現在もPositでtidyverseチームを率いている。

WickhamはIowa State Universityで博士号を取得しており、2008年の博士論文は「Practical Tools for Exploring Data and Models」である。Iowa State Universityの記録では、Dianne Cookが主要指導教員として記載され、Heike Hofmannらも指導に参加している。

関係を簡単に表すと、次のようになる。

> Dianne Cook → 博士課程の指導学生 Hadley Wickham → ggplot2・tidyverse

Cookの専門である統計グラフィックス、高次元データ探索、対話的可視化は、Wickhamによるデータ探索ツールの発展と強く結びついている。

ただし、Grammar of Graphics自体の基礎はLeland Wilkinsonの理論であり、Cookが`ggplot2`を直接設計したという意味ではない。WickhamがWilkinsonの理論を階層的なGrammar of Graphicsとして実装し、R利用者が扱いやすい形にしたのが`ggplot2`である。

CookとWickhamは、単なる師弟関係だけではない。高次元データの可視化に関する`tourr`の研究や、visual inferenceを実装する`nullabor`などでも共同研究・共同開発を行っている。

## Yihui Xieとの関係

Yihui Xieは、`knitr`の開発者として知られ、`bookdown`、`blogdown`、R Markdown関連のシステムや書籍を通じて、Rにおける再現可能なレポート作成を大きく発展させた人物である。

XieもIowa State Universityで博士号を取得している。2013年の博士論文は「Dynamic Graphics and Reporting for Statistics」であり、大学の記録ではDianne Cookが主要指導教員として記載されている。

関係は、次のように表せる。

> Dianne Cook → 博士課程の指導学生 Yihui Xie → knitr・動的レポーティング・R Markdown

Xieの博士論文は、動的グラフィックスと統計レポーティングを扱ったもので、本人も博士論文の主要な構成要素としてanimation、cranvas、knitrを挙げている。

Cookの研究領域である動的・対話的可視化と、Xieが発展させた再現可能な文書作成は、別々の領域ではない。データ、コード、グラフ、説明文を一つの分析過程として統合するという点で連続している。

## 3人の関係

```text
Dianne Cook
├─ Hadley Wickham
│  └─ ggplot2、tidyverse、データ探索の体系化
│
└─ Yihui Xie
   └─ knitr、動的ドキュメント、再現可能なレポーティング
```

Dianne Cookは、単に多数のRパッケージを開発した研究者ではない。博士課程指導と共同研究を通じて、現代のRにおける「可視化・探索」と「再現可能な分析・報告」という二つの大きな流れに影響を与えた人物といえる。

今回のキーノートも、これらの流れと密接に結びついている。

- Grammar of Graphicsによって可視化を体系化する
- visual inferenceによって可視化を推論へ拡張する
- uncertainty-aware visualisationによって不確実性を分析と説明の中に戻す
- これらを再現可能な形で授業・課題・評価に組み込む

この意味で、本講演は単なる「グラフ教育」の提案ではない。統計教育において、探索、推論、説明、再現可能性を一つの活動として捉え直そうとする提案である。

## まとめ

この講演から得られる最も重要なメッセージは、**可視化は分析の前段階でも、結果を飾る最後の工程でもなく、統計的推論の中心に置くことができる**ということである。

もし統計教育の最初からこのように可視化を教えれば、学生はグラフを「作る」だけではなく、グラフを通じて仮説を立て、偶然変動と比較し、不確実性を考慮しながら主張を組み立てるようになる。

Cookが最後に投げかけている問いは、統計専攻者だけでなく、他分野で統計を学ぶ学生にとっても重要である。

> 最初から可視化を推論として教えたなら、より統計リテラシーの高い卒業生を育てられるのではないか。

---

## 参考資料

- ICOTS12 programme: Dianne Cook, “Towards a Richer Statistical Thinking: Teaching Visualisation as a Tool for Inference”
- Dianne Cook, Monash University: https://research.monash.edu/en/persons/dianne-cook
- `nullabor` package: https://cran.r-project.org/package=nullabor
- Hadley Wickham, “Practical Tools for Exploring Data and Models,” Iowa State University Digital Repository: https://dr.lib.iastate.edu/handle/20.500.12876/69291
- Hadley Wickham, Posit profile: https://opensource.posit.co/people/hadley-wickham/
- Yihui Xie, “Dynamic Graphics and Reporting for Statistics,” Iowa State University Digital Repository: https://dr.lib.iastate.edu/etd/13518/
- Yihui Xie, Curriculum Vitae: https://yihui.org/en/vitae/
- Yihui Xie, `knitr`: https://yihui.org/knitr/
