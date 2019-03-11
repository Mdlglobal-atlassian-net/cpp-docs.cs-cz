---
title: '&lt;Param&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- param
- <param>
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
ms.openlocfilehash: 33288b170dc89ad9fd7bbf33fece11c396f45295
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743239"
---
# <a name="ltparamgt-visual-c"></a>&lt;Param&gt; (Visual C++)

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

Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

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

[Dokumentace XML](../ide/xml-documentation-visual-cpp.md)
