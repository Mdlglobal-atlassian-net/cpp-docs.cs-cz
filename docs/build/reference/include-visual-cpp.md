---
title: '&lt;zahrnout > (C++ dokumentační komentáře)'
ms.date: 11/04/2016
f1_keywords:
- <include>
helpviewer_keywords:
- include C++ XML tag
- <include> C++ XML tag
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
ms.openlocfilehash: e1d6a26f28069cfb4a1c74bd591d63bc89352774
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439517"
---
# <a name="ltincludegt"></a>&lt;include&gt;

\<include > umožňuje odkazování na komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu. Toto je alternativa k umístění dokumentačních komentářů přímo do souboru zdrojového kódu.  Můžete například použít \<zahrnout > pro vložení standardních "často používaných" komentářů, které se používají v celém týmu nebo společnosti.

## <a name="syntax"></a>Syntaxe

```
<include file='filename' path='tagpath' />
```

#### <a name="parameters"></a>Parametry

*Bitmap*<br/>
Název souboru, který obsahuje dokumentaci. Název souboru může být kvalifikován cestou.  Název uzavřete do jednoduchých nebo dvojitých uvozovek.  Kompilátor vydá upozornění, pokud nenajde `filename`.

*tagpath*<br/>
Platný výraz XPath, který vybírá požadovanou sadu uzlů obsaženou v souboru.

*Jméno*<br/>
Specifikátor názvu ve značce, který předchází komentářům; `name` bude mít `id`.

*id*<br/>
ID značky, která předchází komentář.  Název uzavřete do jednoduchých nebo dvojitých uvozovek.

## <a name="remarks"></a>Poznámky

\<obsahuje značku > používá syntaxi XPath XML. V dokumentaci XPath najdete způsoby přizpůsobení pomocí \<include >.

Zkompilujte pomocí [/doc](doc-process-documentation-comments-c-cpp.md) a zpracujte dokumentační komentáře do souboru.

## <a name="example"></a>Příklad

Toto je příklad vícesouborového typu. První soubor, který používá \<include >, obsahuje následující komentáře k dokumentaci:

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

Druhý soubor xml_include_tag. doc obsahuje následující komentáře k dokumentaci:

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

[Dokumentace XML](xml-documentation-visual-cpp.md)
