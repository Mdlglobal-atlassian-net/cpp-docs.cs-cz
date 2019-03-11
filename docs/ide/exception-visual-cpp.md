---
title: '&lt;výjimka&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: f30ae7e36c0540c98eecf2c9f73fbd23df230663
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748187"
---
# <a name="ltexceptiongt-visual-c"></a>&lt;výjimka&gt; (Visual C++)

\<Výjimky > značky umožňuje určit, jaké výjimky mohou být vyvolány. Tato značka se použije k definici metody.

## <a name="syntax"></a>Syntaxe

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>Parametry

*Člen*<br/>
Odkaz na výjimku, která je k dispozici z prostředí aktuální kompilace. Pomocí pravidel vyhledávání pro název, kompilátor kontroluje, zda existuje výjimka a přeloží `member` k názvu canonical prvku ve výstupním souboru XML.  Kompilátor vyvolá upozornění, pokud se nenajde `member`.

Název uzavřete do jednoduchých nebo dvojitých uvozovek.

Informace o tom, jak vytvořit cref odkaz na obecný typ, naleznete v tématu [ \<naleznete v tématu >](../ide/see-visual-cpp.md).

*description*<br/>
Popis.

## <a name="remarks"></a>Poznámky

Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

Kompilátor Visual C++ se pokusí přeložit odkazy cref v jednom průchodu přes komentáře k dokumentaci.  Proto pokud pomocí pravidel vyhledávání C++ symbol nebyl nalezen kompilátorem odkaz bude označen jako nevyřešené. Zobrazit [ \<seealso >](../ide/seealso-visual-cpp.md) Další informace.

## <a name="example"></a>Příklad

```
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

[Dokumentace XML](../ide/xml-documentation-visual-cpp.md)
