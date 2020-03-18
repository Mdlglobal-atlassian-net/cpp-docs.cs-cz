---
title: '> &lt;výjimky (C++ dokumentační dokumentace)'
ms.date: 11/04/2016
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: d56e0ce7c892cfd9fd909b5268043d77929bd43c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439859"
---
# <a name="ltexceptiongt"></a>výjimka &lt;&gt;

Značka > \<výjimky umožňuje určit, které výjimky mohou být vyvolány. Tato značka se aplikuje na definici metody.

## <a name="syntax"></a>Syntaxe

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>Parametry

*člen*<br/>
Odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace. Při použití pravidel vyhledávání názvů kompilátor kontroluje, zda daná výjimka existuje, a překládá `member` na název kanonického prvku ve výstupním souboru XML.  Kompilátor vydá upozornění, pokud nenajde `member`.

Název uzavřete do jednoduchých nebo dvojitých uvozovek.

Informace o tom, jak vytvořit odkaz cref na obecný typ, najdete v tématu [\<>](see-visual-cpp.md).

*název*<br/>
Popis.

## <a name="remarks"></a>Poznámky

Zkompilujte pomocí [/doc](doc-process-documentation-comments-c-cpp.md) a zpracujte dokumentační komentáře do souboru.

Kompilátor MSVC se pokusí vyřešit odkazy cref v jednom průchodu pomocí dokumentačních komentářů.  Proto pokud použijete pravidla C++ vyhledávání, symbol nebyl nalezen kompilátorem, odkaz bude označen jako nevyřešený. Další informace najdete v tématu [\<seealso >](seealso-visual-cpp.md) .

## <a name="example"></a>Příklad

```cpp
// xml_exception_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_exception_tag.dll
using namespace System;

/// Text for class EClass.
public ref class EClass : public Exception {
   // class definition ...
};

/// <exception cref="System.Exception">Thrown when... .</exception>
public ref class TestClass {
   void Test() {
      try {
      }
      catch(EClass^) {
      }
   }
};
```

## <a name="see-also"></a>Viz také

[Dokumentace XML](xml-documentation-visual-cpp.md)
