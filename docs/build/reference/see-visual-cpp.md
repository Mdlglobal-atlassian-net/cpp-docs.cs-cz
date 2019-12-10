---
title: '&lt;Zobrazit > (C++ dokumentační komentáře)'
ms.date: 11/04/2016
f1_keywords:
- <see>
- see
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: 8693646fa37648d1b20c791d99d159f2c81b8ec1
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988627"
---
# <a name="ltseegt"></a>&lt;zobrazit&gt;

\<Zobrazit značku > umožňuje zadat odkaz v rámci textu. Pomocí [\<seealso >](seealso-visual-cpp.md) označíte text, který se může objevit v části Viz také.

## <a name="syntax"></a>Syntaxe

```
<see cref="member"/>
```

#### <a name="parameters"></a>Parametry

*člen*<br/>
Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.  Název uzavřete do jednoduchých nebo dvojitých uvozovek.

Kompilátor kontroluje, zda daný prvek kódu existuje, a překládá `member` na název elementu ve výstupním souboru XML.  Kompilátor vydá upozornění, pokud nenajde `member`.

## <a name="remarks"></a>Poznámky

Zkompilujte pomocí [/doc](doc-process-documentation-comments-c-cpp.md) a zpracujte dokumentační komentáře do souboru.

Příklad použití \<> naleznete v tématu [\<summary >](summary-visual-cpp.md) .

Kompilátor MSVC se pokusí vyřešit odkazy cref v jednom průchodu pomocí dokumentačních komentářů.  Proto pokud použijete pravidla C++ vyhledávání, symbol nebyl nalezen kompilátorem, odkaz bude označen jako nevyřešený. Další informace najdete v tématu [\<seealso >](seealso-visual-cpp.md) .

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak lze vytvořit odkaz cref na obecný typ, například, kompilátor vyřeší odkaz.

```cpp
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
