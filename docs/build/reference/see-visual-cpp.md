---
title: '&lt;Zobrazit > (C++ dokumentačních komentářů)'
ms.date: 11/04/2016
f1_keywords:
- <see>
- see
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: be99d3ac156c587888a7c56997d82531cf86ccec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318898"
---
# <a name="ltseegt"></a>&lt;V tématu&gt;

\<Naleznete v tématu > značky umožňuje zadat odkaz v rámci textu. Použití [ \<seealso >](seealso-visual-cpp.md) označuje text, který chcete zobrazit v části Viz také.

## <a name="syntax"></a>Syntaxe

```
<see cref="member"/>
```

#### <a name="parameters"></a>Parametry

*Člen*<br/>
Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.  Název uzavřete do jednoduchých nebo dvojitých uvozovek.

Kompilátor kontroluje, zda daný prvek kódu existuje a odstraňuje `member` do názvu prvku ve výstupním souboru XML.  Kompilátor vyvolá upozornění, pokud se nenajde `member`.

## <a name="remarks"></a>Poznámky

Kompilovat s [/doc](doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

Zobrazit [ \<summary >](summary-visual-cpp.md) pro příklad použití \<naleznete v tématu >.

Kompilátor MSVC pokusila přeložit odkazy cref v jednom průchodu přes komentáře k dokumentaci.  Proto pokud pomocí pravidel vyhledávání C++ symbol nebyl nalezen kompilátorem odkaz bude označen jako nevyřešené. Zobrazit [ \<seealso >](seealso-visual-cpp.md) Další informace.

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

## <a name="see-also"></a>Viz také:

[Dokumentace XML](xml-documentation-visual-cpp.md)
