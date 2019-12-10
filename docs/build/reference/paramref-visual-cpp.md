---
title: '&lt;paramref > (C++ dokumentační dokumentace)'
ms.date: 11/04/2016
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- paramref C++ XML tag
- <paramref> C++ XML tag
ms.assetid: c5730dc2-7159-421f-b2d5-bb971e307122
ms.openlocfilehash: 1f4e9cb0e6b39e4da78e78048342dac2ecc9deea
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988687"
---
# <a name="ltparamrefgt"></a>&lt;paramref&gt;

Značka > \<paramref poskytuje způsob, jak označit, že slovo je parametrem. Soubor. XML může být zpracován pro naformátování tohoto parametru nějakým odlišným způsobem.

## <a name="syntax"></a>Syntaxe

```
<paramref name="name"/>
```

#### <a name="parameters"></a>Parametry

*name*<br/>
Název parametru, na který se má odkazovat  Název uzavřete do jednoduchých nebo dvojitých uvozovek.  Kompilátor vydá upozornění, pokud nenajde `name`.

## <a name="remarks"></a>Poznámky

Zkompilujte pomocí [/doc](doc-process-documentation-comments-c-cpp.md) a zpracujte dokumentační komentáře do souboru.

## <a name="example"></a>Příklad

```cpp
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

## <a name="see-also"></a>Viz také:

[Dokumentace XML](xml-documentation-visual-cpp.md)
