---
title: C2511 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2511
dev_langs:
- C++
helpviewer_keywords:
- C2511
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d97cbbd75d3b39b55ff640ed99e261ba349043d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199625"
---
# <a name="compiler-error-c2511"></a>C2511 chyby kompilátoru
"identifikátor": přetížený – členská funkce nebyla nalezena v 'class'.  
  
 Žádná verze funkce je deklarovaná se zadanými parametry.  Možné příčiny:  
  
1.  Funkce předány nesprávné parametry.  
  
2.  Parametry předaný nesprávném pořadí.  
  
3.  Nesprávný pravopis názvů parametrů.  
  
 Následující ukázka generuje C2511:  
  
```  
// C2511.cpp  
// compile with: /c  
class C {  
   int c_2;  
   int Func(char *, char *);  
};  
  
int C::Func(char *, char *, int i) {   // C2511  
// try the following line instead  
// int C::Func(char *, char *) {  
   return 0;  
}  
```