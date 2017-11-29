---
title: "C3366 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3366
dev_langs: C++
helpviewer_keywords: C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b862e606b86eca0a7eb7f2ad1e91f2776c8c0b23
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3366"></a>C3366 chyby kompilátoru
"proměnné": spravované členy statických dat nebo WinRTtypes musí být definován v rámci definice třídy  
  
 Pokoušíte se o odkaz je statický člen WinRT nebo rozhraní .NET třídy nebo rozhraní mimo definici třídy nebo rozhraní.  
  
 Kompilátor musí znát úplné definice třídy (pro vydávání meta-data po jednom průchodu) a vyžaduje členy statických dat na inicializaci v rámci třídy.  
  
 Například v následujícím příkladu generuje C3366 a ukazuje, jak to opravit:  
  
```  
// C3366.cpp  
// compile with: /clr /c  
ref class X {  
   public:  
   static int i;   // initialize i here to avoid C3366  
};  
  
int X::i = 5;      // C3366  
```  