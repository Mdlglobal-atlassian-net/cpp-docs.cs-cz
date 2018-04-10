---
title: '&lt;zahrnout&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-ide
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- include
- <include>
dev_langs:
- C++
helpviewer_keywords:
- include C++ XML tag
- <include> C++ XML tag
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f9a6b07ce540d67a44e46a24fb943dac93bb95a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ltincludegt-visual-c"></a>&lt;zahrnout&gt; (Visual C++)
\<Zahrnují > značka umožňuje odkazovat komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu. Jde o alternativu k uvedení dokumentační komentáře ve zdrojovém kódu souboru přímo.  Například můžete použít \<zahrnují > Vložit standardní "standardní" komentáře, které se používají v rámci váš tým nebo společnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<include file='filename' path='tagpath' />  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Název souboru, který obsahuje v dokumentaci. Název souboru může být kvalifikovaný s cestou.  Uzavřete název v jednoduchých nebo dvojitých uvozovek.  Kompilátor vydá upozornění, pokud jej nenalezne `filename`.  
  
 `tagpath`  
 Platný výraz XPath, který vybere požadované sady uzlů obsažené v souboru.  
  
 `name`  
 Specifikátor název ve značce, která předchází komentáře; `name` bude mít `id`.  
  
 `id`  
 ID značky, která předchází komentáře.  Uzavřete název v jednoduchých nebo dvojitých uvozovek.  
  
## <a name="remarks"></a>Poznámky  
 \<Zahrnují > Značka se používá syntaxe XML XPath. Výraz XPath dokumentaci k tom, jak přizpůsobit pomocí \<zahrnují >.  
  
 Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Toto je příklad více souborů. První soubor, který používá \<zahrnují >, obsahuje následující dokumentační komentáře:  
  
```  
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
  
 Druhý soubor, xml_include_tag.doc, obsahuje následující dokumentační komentáře:  
  
```  
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
  
```  
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