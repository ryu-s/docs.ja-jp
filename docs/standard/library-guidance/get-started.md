---
title: 高品質な .NET ライブラリの作成の概要
description: .NET ライブラリの構築を始めましょう。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 6377e3fe606bf7603b418decdd0e3f9d2de6a510
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201244"
---
# <a name="get-started"></a>作業開始

## <a name="cross-platform-targetingcross-platform-targetingmd"></a>[クロス プラットフォーム ターゲット](./cross-platform-targeting.md)

.NET Standard およびマルチ ターゲットを使用してクロスプラットフォーム ライブラリを作成する方法について。 .NET はさまざまな場所で実行されるため、優れた .NET ライブラリは、できるだけ多くのプラットフォームと開発者をサポートするために存続する必要があります。

## <a name="strong-namingstrong-namingmd"></a>[厳密な名前付け](./strong-naming.md)

厳密な名前付けとその長所と短所について説明します。 .NET ライブラリの厳密な名前付けにより多くの開発者が使用できるようになるため、これは推奨されるベスト プラクティスです。

## <a name="nuget-and-open-source-librariesnugetmd"></a>[NuGet およびオープン ソース ライブラリ](./nuget.md)

NuGet.org で一般公開されているすべてのパッケージに推奨されるメタデータを含むオープン ソースの .NET ライブラリで NuGet パッケージを作成する最善の方法です。

### <a name="dependenciesdependenciesmd"></a>[依存関係](./dependencies.md)

NuGet により、.NET ライブラリの構築時に既存のパッケージが使いやすくなります。 NuGet の依存関係の一般的な競合原因と、その回避方法について説明します。

### <a name="sourcelinksourcelinkmd"></a>[SourceLink](./sourcelink.md)

SourceLink は、.NET ライブラリのユーザーがデバッグ中にそのソース コードにステップ インできるようにする優れたツールです。 この記事では、SourceLink とは何かと、それを使用する理由の概要を示します。

### <a name="publishingpublish-nuget-packagemd"></a>[発行](./publish-nuget-package.md)

NuGet.org は最も広く知られ、使用されているリポジトリで、NuGet パッケージを発行する場所は数多くあります。 使用可能な NuGet パッケージ リポジトリのそれぞれの違いと、.NET ライブラリを発行するためのセキュリティのベスト プラクティスについて説明します。

## <a name="versioningversioningmd"></a>[バージョン管理](./versioning.md)

優れた .NET ライブラリは時間の経過と共に進化し、機能が追加され、バグが修正され、後のリリースになるほどパフォーマンスが向上します。 各バージョン番号と、破壊的変更を開発者に伝える方法について説明します。

### <a name="breaking-changesbreaking-changesmd"></a>[破壊的変更](./breaking-changes.md)

.NET ライブラリでは既存のユーザーに向けた安定性と将来に向けたイノベーションとの間でバランスを取ることが重要です。 さまざまな種類の破壊的変更と、下位互換性を維持しながら新しい機能を追加するための戦略について説明します。

>[!div class="step-by-step"]
[前へ](./index.md)
[次へ](./cross-platform-targeting.md)
