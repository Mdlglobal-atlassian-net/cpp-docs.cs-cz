---
title: '&lt;Param > (C++ dokumentačních komentářů)'
ms.date: 11/04/2016
f1_keywords:
- param
- <param>
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
ms.openlocfilehash: d8ea4feddbe1ec2d5898f8ef698cc2d69d255933
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823045"
---
# <a name="ltparamgt"></a>&lt;param&gt;

\<Param > značky byste měli použít ve komentář pro deklaraci metody, popisující jeden z parametrů pro metodu.

## <a name="syntax"></a>Syntaxe

```
<param name='name'>description</param>
```

#### <a name="parameters"></a>Parametry

*Jméno*<br/>
Název parametru metody.  Název uzavřete do jednoduchých nebo dvojitých uvozovek.  Kompilátor vyvolá upozornění, pokud se nenajde `name`.

*description*<br/>
Popis pro parametr.

## <a name="remarks"></a>Poznámky

Text \<param > značky se zobrazí v IntelliSense, [prohlížeče objektů](/visualstudio/ide/viewing-the-structure-of-code)a v sestavě webového kódu komentář.

Kompilovat s [/doc](doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

## <a name="example"></a>Příklad

```cpp
// xml_param_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_param_tag.dll
/// Text for class MyClass.
public ref class MyClass {
   /// <param name="Int1">Used to indicate status.</param>
   void MyMethod(int Int1) {
   }
};
```

## <a name="see-also"></a>Viz také:

[Dokumentace XML](xml-documentation-visual-cpp.md)
