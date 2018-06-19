---
title: C2884 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2884
dev_langs:
- C++
helpviewer_keywords:
- C2884
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41bacfc53f8b1f14a9b7409a43db39fd943739e5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33261465"
---
# <a name="compiler-error-c2884"></a>C2884 chyby kompilátoru
"název": zaváděné pomocí deklarace je v konfliktu s místní funkce 'function'.  
  
 Pokusili jste se definovat funkce více než jednou. První definice je místní definice. Druhá je z oboru názvů s `using` deklarace.  
  
 Následující ukázka generuje C2884:  
  
```  
// C2884.cpp  
namespace A {  
   void z(int);  
}  
  
void f() {  
   void z(int);  
   using A::z;   // C2884 z is already defined  
}  
```