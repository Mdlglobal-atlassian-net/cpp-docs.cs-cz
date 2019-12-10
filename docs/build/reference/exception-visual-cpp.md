---
title: '> &lt;výjimky (C++ dokumentační dokumentace)'
ms.date: 11/04/2016
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: ddfe647fa2db55b3ca606265011896a66398a8a2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988290"
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

Informace o tom, jak vytvořit odkaz cref na obecný typ, najdete v tématu [\<](see-visual-cpp.md).

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

## <a name="see-also"></a>Viz také:

[Dokumentace XML](xml-documentation-visual-cpp.md)
