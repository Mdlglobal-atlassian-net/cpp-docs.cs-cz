---
title: "Kompilátoru (úroveň 3) upozornění C4637 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4637
dev_langs: C++
helpviewer_keywords: C4637
ms.assetid: 5fd347c1-2de9-408f-9136-1bf1ff273622
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a183977d32594d63e0b5d8a8c65e32372940e1f4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4637"></a>C4637 kompilátoru upozornění (úroveň 3)
Cíl komentář dokumentu XML: \<zahrnují > Značka zahozeny.  Důvod  
  
 Syntaxe [ \<zahrnují >](../../ide/include-visual-cpp.md) značky nebyl zadán správně.  
  
 Následující ukázka generuje C4637:  
  
```  
// C4637.cpp  
// compile with: /clr /doc /LD /W3  
using namespace System;  
  
/// Text for class MyClass.  
public ref class MyClass {   
public:  
   /// <include file="c:\davedata\jtest\xml_include.doc"/>  
   // Try the following line instead:  
   // /// <include file='xml_include.doc' path='MyDocs/MyMembers/*' />  
   void MyMethod() {  
   }  
};   // C4637  
```