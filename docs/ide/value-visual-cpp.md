---
title: '&lt;Hodnota&gt; (Visual C++) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- value
- <value>
dev_langs:
- C++
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a194e45fd79ae59dc91abb21a9fb038d3ec4008
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041685"
---
# <a name="ltvaluegt-visual-c"></a>&lt;Hodnota&gt; (Visual C++)
\<Hodnota > značky umožňuje popisují vlastnosti a metody. Mějte na paměti, že při přidání vlastnosti s kódem průvodce v integrovaném vývojovém prostředí sady Visual Studio přidá [ \<summary >](../ide/summary-visual-cpp.md) značky pro novou vlastnost. Měli byste pak ručně přidat \<hodnota > značka, které popisují hodnotu, která představuje vlastnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>Parametry  
*Popis vlastnosti*<br/>
Popis pro vlastnost.  
  
## <a name="remarks"></a>Poznámky  
 Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
  
```  
// xml_value_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_value_tag.dll  
using namespace System;  
/// Text for class Employee.  
public ref class Employee {  
private:  
   String ^ name;  
   /// <value>Name accesses the value of the name data member</value>  
public:  
   property String ^ Name {  
      String ^ get() {  
         return name;   
      }  
      void set(String ^ i) {  
         name = i;  
      }  
   }  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace XML](../ide/xml-documentation-visual-cpp.md)