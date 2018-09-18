---
title: '&lt;Souhrn&gt; (Visual C++) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <summary>
- summary
dev_langs:
- C++
helpviewer_keywords:
- <summary> C++ XML tag
- summary C++ XML tag
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dae0eef25b11d49e5f869d88862e602d862135c1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082245"
---
# <a name="ltsummarygt-visual-c"></a>&lt;Souhrn&gt; (Visual C++)
\<Summary > Značka by měla sloužit k popisu typu nebo člena typu. Použití [ \<remarks >](../ide/remarks-visual-cpp.md) přidat doplňující informace pro popis typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>Parametry  
*Popis*<br/>
Přehled objektu.  
  
## <a name="remarks"></a>Poznámky  
 Text \<summary > značku je jediný zdroj informací o typu v IntelliSense a zobrazí se také v [Prohlížeč objektů](/visualstudio/ide/viewing-the-structure-of-code) a v sestavě webového kódu komentář.  
  
 Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
  
```  
// xml_summary_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_summary_tag.dll  
  
/// Text for class MyClass.  
public ref class MyClass {  
public:  
   /// <summary>MyMethod is a method in the MyClass class.  
   /// <para>Here's how you could make a second paragraph in a description. <see cref="System::Console::WriteLine"/> for information about output statements.</para>  
   /// <seealso cref="MyClass::MyMethod2"/>  
   /// </summary>  
   void MyMethod(int Int1) {}  
  
   /// text  
   void MyMethod2() {}  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace XML](../ide/xml-documentation-visual-cpp.md)