---
title: 名前空間の使用 (C# プログラミング ガイド)
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 81876d1818a6e82764e4aea0ae2b6f9e091f0ba3
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123398"
---
# <a name="using-namespaces-c-programming-guide"></a>名前空間の使用 (C# プログラミング ガイド)
C# プログラム内では名前空間が 2 つの方法でよく使用されます。 最初の方法では、.NET Framework クラスで名前空間を使用して、その多くのクラスを整理します。 2 つ目の方法では、独自の名前空間を宣言します。これは、より大きなプログラミング プロジェクトでクラス名とメソッド名のスコープを制御するのに役立ちます。  
  
## <a name="accessing-namespaces"></a>名前空間へのアクセス  
 ほとんどの C# アプリケーションは `using` ディレクティブのセクションから始まります。 このセクションには、アプリケーションが頻繁に使用する名前空間がリストされ、包含されているメソッドが使用されるたびにプログラマが完全修飾名を指定しなくても済むようにします。  
  
 たとえば、次の行を記述したとします。  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 この場合、プログラムの開始位置で、以下のコードを使用できます。  
  
 [!code-csharp[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 これは次のコードの代わりに使用します。  
  
 [!code-csharp[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a>名前空間エイリアス  
 [using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md)を使用して、[名前空間](../../../csharp/language-reference/keywords/namespace.md)のエイリアスを作成することもできます。 たとえば、入れ子になった名前空間を含む、以前に作成した名前空間を使用する場合は、次の例のようにエイリアスを宣言して、特定の名前空間を簡単に参照することもできます。  
  
 [!code-csharp[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a>名前空間を使用するスコープの制御  
 `namespace` キーワードを使用して、スコープを宣言します。 プロジェクト内でスコープを作成すると、コードの編成が容易になり、グローバルに一意の型を作成できます。 次の例では、入れ子関係にある 2 つの名前空間で `SampleClass` というクラスを定義します。 [。演算子](../../../csharp/language-reference/operators/member-access-operator.md)を使用して、呼び出されるメソッドを区別します。  
  
 [!code-csharp[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a>完全修飾名  
 名前空間と型には、論理階層を示す完全修飾名で表された一意のタイトルが割り当てられています。 たとえば、ステートメント `A.B` は、`A` が名前空間または型の名前であり、`B` はその内部で入れ子になっていることを意味します。  
  
 入れ子になっているクラスと名前空間を次の例に示します。 完全修飾名は、各エンティティの後のコメントとして示されています。  
  
 [!code-csharp[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 上のコード セグメントの各要素の意味は次のとおりです。  
  
-   名前空間 `N1` はグローバル名前空間のメンバーです。 その完全修飾名は `N1` です。  
  
-   名前空間 `N2` は `N1` のメンバーです。 その完全修飾名は `N1.N2` です。  
  
-   クラス `C1` は `N1` のメンバーです。 その完全修飾名は `N1.C1` です。  
  
-   クラス名 `C2` は、このコードでは 2 回使用されています。 ただし、完全修飾名は異なります。 `C2` の最初のインスタンスは `C1` 内で宣言されているため、その完全修飾名は `N1.C1.C2` となります。 `C2` の 2 つ目のインスタンスは名前空間 `N2` 内で宣言されているため、その完全修飾名は `N1.N2.C2` となります。  
  
 上のコード セグメントを使用して、次のように新しいクラス メンバー `C3` を名前空間 `N1.N2` に追加することができます。  
  
 [!code-csharp[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 通常、`::` は名前空間エイリアスを参照する際に使用し、`global::` はグローバル名前空間を参照する際に使用します。`.` は型またはメンバーを修飾する際に使用します。  
  
 名前空間ではなく型を参照するエイリアスで `::` を使用するのは誤りです。 例:  
  
 [!code-csharp[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 `global` という語は定義済みのエイリアスではないため、`global.X` には特別な意味がないことに注意してください。 `::` と共に使用したときにのみ特別な意味が与えられます。  
  
 `global::` は常にグローバル名前空間を参照し、エイリアスを参照しないので、global という名前のエイリアスを定義すると、コンパイラ警告 CS0440 が生成されます。 たとえば、次のコード行では警告が生成されます。  
  
 [!code-csharp[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 エイリアスで `::` を使用することをお勧めします。そうすれば、追加の型が予想外に導入されることを防ぐことができます。 たとえば、次の例について考えてみます。  
  
 [!code-csharp[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 このコードは動作しますが、`Alias` という名前の型が後で導入された場合、`Alias.` は代わりにその型にバインドされます。 `Alias::Exception` を使用すれば、`Alias` は名前空間エイリアスとして扱われ、型と間違われることがなくなります。  
  
 `global` エイリアスの詳細については、「[方法: グローバル名前空間エイリアスを使用する](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)」を参照してください。  
  
## <a name="see-also"></a>参照

- [C# プログラミングガイド](../../../csharp/programming-guide/index.md)  
- [名前空間](../../../csharp/programming-guide/namespaces/index.md)  
- [名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [。演算子](../../../csharp/language-reference/operators/member-access-operator.md)  
- [:: 演算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [extern](../../../csharp/language-reference/keywords/extern.md)
