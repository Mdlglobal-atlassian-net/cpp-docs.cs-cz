---
title: '&lt;zahrnout&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- include
- <include>
helpviewer_keywords:
- include C++ XML tag
- <include> C++ XML tag
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
ms.openlocfilehash: 0d03ee6e327eb95e63cec16f3886d616c909c3df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451971"
---
# <a name="ltincludegt-visual-c"></a>&lt;zahrnout&gt; (Visual C++)

\<Zahrnout > značky umožňuje odkazovat na komentáře do jiného souboru, které popisují typy a členy ve zdrojovém kódu. Jedná se o alternativu k uvedení dokumentační komentáře přímo v souboru zdrojového kódu.  Například můžete použít \<zahrnout > Chcete-li vložit standardní "standardní" komentáře, které se používají v váš tým nebo společnost.

## <a name="syntax"></a>Syntaxe

```
<include file='filename' path='tagpath' />
```

#### <a name="parameters"></a>Parametry

*Název souboru*<br/>
Název souboru, který obsahuje dokumentaci. Název souboru může být kvalifikovány s cestou.  Název uzavřete do jednoduchých nebo dvojitých uvozovek.  Kompilátor vyvolá upozornění, pokud se nenajde `filename`.

*tagpath*<br/>
Platný výraz XPath, který vybere požadované sadě uzlů obsažené v souboru.

*Jméno*<br/>
Specifikátor názvem ve značce, který předchází komentáře; `name` bude mít `id`.

*id*<br/>
ID značky, které předchází komentáře.  Název uzavřete do jednoduchých nebo dvojitých uvozovek.

## <a name="remarks"></a>Poznámky

\<Zahrnout > značky používá syntaxe jazyka XML. Výraz XPath dokumentaci způsoby, jak přizpůsobit pomocí \<zahrnout >.

Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

## <a name="example"></a>Příklad

Toto je vícesouborové příklad. První soubor, který používá \<zahrnout >, obsahuje následující komentáře k dokumentaci:

```cpp
// xml_include_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_include_tag.dll

/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test"]/*' />
public ref class Test {
   void TestMethod() {
   }
};

/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test2"]/*' />
public ref class Test2 {
   void Test() {
   }
};
```

Druhý soubor, xml_include_tag.doc, obsahuje následující komentáře k dokumentaci:

```xml
<MyDocs>

<MyMembers name="test">
<summary>
The summary for this type.
</summary>
</MyMembers>

<MyMembers name="test2">
<summary>
The summary for this other type.
</summary>
</MyMembers>

</MyDocs>
```

## <a name="program-output"></a>Výstup programu

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>t2</name>
    </assembly>
    <members>
        <member name="T:Test">
            <summary>
The summary for this type.
</summary>
        </member>
        <member name="T:Test2">
            <summary>
The summary for this other type.
</summary>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a>Viz také

[Dokumentace XML](../ide/xml-documentation-visual-cpp.md)