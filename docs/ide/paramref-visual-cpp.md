---
title: '&lt;paramref&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- paramref C++ XML tag
- <paramref> C++ XML tag
ms.assetid: c5730dc2-7159-421f-b2d5-bb971e307122
ms.openlocfilehash: 32ed64bc4d76e75dc7de47f8f3bd3c7ab5823cdc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586301"
---
# <a name="ltparamrefgt-visual-c"></a>&lt;paramref&gt; (Visual C++)

\<Paramref > značky poskytuje způsob, jak určit, že je slovo parametru. Soubor XML mohou být zpracovány k nějakým způsobem odlišné formátování tento parametr.

## <a name="syntax"></a>Syntaxe

```
<paramref name="name"/>
```

#### <a name="parameters"></a>Parametry

*Jméno*<br/>
Název parametru jako reference.  Název uzavřete do jednoduchých nebo dvojitých uvozovek.  Kompilátor vyvolá upozornění, pokud se nenajde `name`.

## <a name="remarks"></a>Poznámky

Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

## <a name="example"></a>Příklad

```
// xml_paramref_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_paramref_tag.dll
/// Text for class MyClass.
public ref class MyClass {
   /// <summary>MyMethod is a method in the MyClass class.
   /// The <paramref name="Int1"/> parameter takes a number.
   /// </summary>
   void MyMethod(int Int1) {}
};
```

## <a name="see-also"></a>Viz také

[Dokumentace XML](../ide/xml-documentation-visual-cpp.md)