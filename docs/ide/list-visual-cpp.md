---
title: '&lt;seznam&gt; (Visual C++) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- list
- <list>
dev_langs: C++
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e04fb5f7ff2ba22b53c0fe163455bfdb666f9b9f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ltlistgt-visual-c"></a>&lt;seznam&gt; (Visual C++)
\<Listheader > blokování se používá k definování řádek záhlaví tabulky nebo definice seznamu. Při definování tabulku, stačí zadat položku termín v záhlaví.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<list type="bullet" | "number" | "table">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### <a name="parameters"></a>Parametry  
 `term`  
 Termín, definovat, které budou určené v `description`.  
  
 `description`  
 Buď položku v odrážku nebo číslovaný seznam nebo definice `term`.  
  
## <a name="remarks"></a>Poznámky  
 Každá položka v seznamu je definován s \<položky > bloku. Při vytváření definice seznamu, budete muset zadat oba seznamy `term` a `description`. Ale pro tabulku, seznamu s odrážkami nebo číslovaný seznam, stačí zadat položku pro `description`.  
  
 Seznam nebo tabulka může mít jako mnoho \<položky > blokuje podle potřeby.  
  
 Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
  
```  
// xml_list_tag.cpp  
// compile with: /doc /LD  
// post-build command: xdcmake xml_list_tag.dll  
/// <remarks>Here is an example of a bulleted list:  
/// <list type="bullet">  
/// <item>  
/// <description>Item 1.</description>  
/// </item>  
/// <item>  
/// <description>Item 2.</description>  
/// </item>  
/// </list>  
/// </remarks>  
class MyClass {};  
```  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace XML](../ide/xml-documentation-visual-cpp.md)