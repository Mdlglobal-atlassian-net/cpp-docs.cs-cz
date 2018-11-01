---
title: '&lt;Zobrazit&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- <see>
- see
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: f5fa63f2dbd97f0a2da98a5a31a1192e40599738
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461357"
---
# <a name="ltseegt-visual-c"></a>&lt;Zobrazit&gt; (Visual C++)

\<Naleznete v tématu > značky umožňuje zadat odkaz v rámci textu. Použití [ \<seealso >](../ide/seealso-visual-cpp.md) označuje text, který chcete zobrazit v části Viz také.

## <a name="syntax"></a>Syntaxe

```
<see cref="member"/>
```

#### <a name="parameters"></a>Parametry

*Člen*<br/>
Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.  Název uzavřete do jednoduchých nebo dvojitých uvozovek.

Kompilátor kontroluje, zda daný prvek kódu existuje a odstraňuje `member` do názvu prvku ve výstupním souboru XML.  Kompilátor vyvolá upozornění, pokud se nenajde `member`.

## <a name="remarks"></a>Poznámky

Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

Zobrazit [ \<summary >](../ide/summary-visual-cpp.md) pro příklad použití \<naleznete v tématu >.

Kompilátor Visual C++ se pokusí přeložit odkazy cref v jednom průchodu přes komentáře k dokumentaci.  Proto pokud pomocí pravidel vyhledávání C++ symbol nebyl nalezen kompilátorem odkaz bude označen jako nevyřešené. Zobrazit [ \<seealso >](../ide/seealso-visual-cpp.md) Další informace.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak můžete provést cref odkaz na obecný typ, tak, že kompilátor bude přeložit odkaz.

```
// xml_see_cref_example.cpp
// compile with: /LD /clr /doc
// the following cref shows how to specify the reference, such that,
// the compiler will resolve the reference
/// <see cref="C{T}">
/// </see>
ref class A {};

// the following cref shows another way to specify the reference,
// such that, the compiler will resolve the reference
/// <see cref="C < T >"/>

// the following cref shows how to hard-code the reference
/// <see cref="T:C`1">
/// </see>
ref class B {};

/// <see cref="A">
/// </see>
/// <typeparam name="T"></typeparam>
generic<class T>
ref class C {};
```

## <a name="see-also"></a>Viz také

[Dokumentace XML](../ide/xml-documentation-visual-cpp.md)