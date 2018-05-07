---
title: C3366 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3366
dev_langs:
- C++
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c26bfbb5d66ad22484184bd361f14004ed8aa30c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
