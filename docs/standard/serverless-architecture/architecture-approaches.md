---
title: サーバーレス アプリのアーキテクチャ アプローチ
description: アーキテクチャの概要については、サーバーレスに N 層アーキテクチャからのクラウド ベースのエンタープライズ アプリケーションを構築するために近くなります。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 21e191f17e7d0b4f2d64454fb14c46a4831a8375
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "49370283"
---
# <a name="architecture-approaches"></a>アーキテクチャのアプローチ

エンタープライズ アプリの設計に既存のアプローチを理解するのに役立ちますはサーバーレスが果たす役割を明確にすることにします。 多くの方法や、ソフトウェア開発の数十年にわたって進化してパターンが存在し、独自の長所と短所があるすべて。 多くの場合、究極のソリューションは 1 つのアプローチを決定する必要がありますされませんが、いくつかのアプローチを統合することがあります。 移行シナリオには、多くの場合、1 つのアーキテクチャ アプローチからハイブリッド アプローチを通じて別に移行が含まれます。

この章では、エンタープライズ アプリケーションの両方の論理および物理アーキテクチャ パターンの概要を説明します。

## <a name="architecture-patterns"></a>アーキテクチャ パターン

最新のビジネス アプリケーションでは、さまざまなアーキテクチャ パターンに従います。 このセクションでは、一般的なパターンの調査を表します。 ここで示したパターンでは、必ずしもすべてのベスト プラクティスはありませんが、さまざまな方法を示しています。

詳細については、次を参照してください。 [Azure アプリケーション アーキテクチャ ガイド](https://docs.microsoft.com/azure/architecture/guide/)します。

## <a name="monoliths"></a>モノリス

多くのビジネス アプリケーションでは、モノリス パターンに従います。 多くの場合、レガシ アプリケーションは、モノリスとして実装されます。 モノリシック パターンでは、すべてのアプリケーションの問題は、1 つの配置に格納されます。 同じコードベースにはデータベース呼び出しをユーザー インターフェイスからすべてのものが含まれます。

![モノリシック アーキテクチャ](./media/monolith-architecture.png)

モノリシック アプローチをいくつかの利点があります。 1 つのコード ベースをプルし、作業開始することがよくあります。 ランプ アップ時間は、小さい可能性があり、新しいコピーを提供するだけでは、テスト環境を作成します。 複数のコンポーネントとアプリケーションを含む、モノリスを設計することがあります。

残念ながら、モノリシック パターンは、大規模に分類する傾向があります。 モノリシック アプローチの大きな欠点は次のとおりです。

* 同じコード ベースで並列処理が難しくなっています。
* どのように簡単に関係なく、任意の変更は、アプリケーション全体の新しいバージョンを展開する必要があります。
* リファクタリングの可能性がある、アプリケーション全体に影響します。
* スケールする唯一のソリューションは複数作成する、多くの場合、モノリスのコピーをリソースを消費します。
* システムを展開するか、またはその他のシステムは、取得、統合が難しいことができます。
* 全体のモノリスを構成する必要性のためのテストが難しいことがあります。
* コードの再利用が困難と多くの場合、その他のアプリが最終的にコードの独自のコピーを保持します。

多くの企業は、クラウドにモノリシック アプリケーションを移行し、同時に利用可能なパターンの詳細にそれらをリファクターするチャンスとなります。 管理、展開、およびを個別にスケーリングするためには、個々 のアプリケーションとコンポーネントを一般的です。

## <a name="n-layer-applications"></a>N 層アプリケーション

N 層アプリケーションの特定のレイヤーにアプリケーション ロジックをパーティション。 最も一般的なレイヤーは、次のとおりです。

* [ユーザー インターフェイス]
* ビジネス ロジック
* データ アクセス

他のレイヤーには、ミドルウェア、バッチ処理、および API を含めることができます。 レイヤーは論理的に注意して重要です。 分離で開発する、ですが、すべて展開することが、同じターゲット プラットフォーム。

![N 層アーキテクチャ](./media/n-layer-architecture.png)

N 層のアプローチをいくつかの利点があるなど。

* リファクタリングは、レイヤーに分離されます。
* チームできます個別にビルド、テスト、展開、および別のレイヤーを維持します。
* レイヤーをスワップ アウト、たとえば、データ層は UI レイヤーに変更することがなく複数のデータベースをアクセス可能性があります。

サーバーレスは、1 つまたは複数のレイヤーを実装するために使用できます。

## <a name="microservices"></a>マイクロサービス

**[マイクロ サービス](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** アーキテクチャが含まれる共通の特徴を含みます。

* アプリケーションは、いくつかの小さなサービスで構成されます。
* 各サービスは、独自のプロセスで実行されます。
* サービスは、ビジネス ドメインの周囲に配置されます。
* サービスは、通常、トランスポートとして HTTP を使用して軽量の Api 経由で通信します。
* サービスのデプロイし、は個別にアップグレードできます。
* サービスが 1 つのデータ ストアに依存します。
* システムはエラーを考慮して設計されていて、アプリには、特定のサービスが失敗する場合でも引き続きを実行できます。

マイクロ サービスは、他のアーキテクチャのアプローチを相互に排他的にする必要はありません。 たとえば、N 層アーキテクチャでは、中間層のマイクロ サービスを使用できます。 さまざまなコンテナーに IIS ホスト上の仮想ディレクトリからの方法でマイクロ サービスを実装することもできます。 マイクロ サービスの特性となってサーバーレスの実装に特に適しています。

![マイクロサービス アーキテクチャ](./media/microservices-architecture.png)

マイクロ サービス アーキテクチャの利点は次のとおりです。

* リファクタリングは、1 つのサービスに分離では多くの場合です。
* サービスは、それぞれ個別にアップグレードできます。
* 回復性と弾力性は、個々 のサービスのニーズに合わせて調整できます。
* 開発がさまざまなチームおよびプラットフォーム間で並列に発生します。
* 分離サービスの包括的なテストを記述しやすくなります。

マイクロ サービスなど、独自の課題が付属します。

* どのようなサービスを利用し、これらを呼び出す方法を決定します。
* サービスのライフ サイクルを管理します。
* サービスをまとめる方法でアプリケーション全体について理解します。
* 完全なシステムは、異なるサービス間で行われた呼び出しのテスト。

最終的には、すべての後で説明するサーバーレスのメリットを利用することを含め、これらの課題に対応するソリューションがあります。

>[!div class="step-by-step"]
[前へ](index.md)
[次へ](architecture-deployment-approaches.md)
