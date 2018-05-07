---
title: C2733 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2733
dev_langs:
- C++
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc1857cd800dd2d395754b9ae95094d9f57aad27
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2733"></a>C2733 chyby kompilátoru
druhý C propojení přetížené funkce nejsou povoleny funkce  
  
 Více než jednu deklaraci přetížené funkce s C propojení. Pokud používáte C propojení, může být pouze jednu formu zadaná funkce externí. Vzhledem k tomu, že přetížených funkcí mají stejný název bez upraveného, nelze použít s programy C.  
  
 Následující ukázka generuje C2733:  
  
```  
// C2733.cpp  
extern "C" {  
   void F1(int);  
}  
  
extern "C" {  
   void F1();   // C2733  
   // try the following line instead  
   // void F2();  
}  
```