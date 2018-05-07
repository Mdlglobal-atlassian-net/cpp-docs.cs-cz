---
title: C2803 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2803
dev_langs:
- C++
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51cf2a8b38a86fcd97ab693b3853fe25527a0bb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2803"></a>C2803 chyby kompilátoru
'operátor operátor' musí mít alespoň jeden formální parametr typu třídy  
  
 Přetížené operátor chybí parametr typu třídy.  
  
 Je třeba předat minimálně jeden parametr odkazem (není pomocí ukazatele, ale odkazů) nebo hodnota, která má být schopni zapisovat "< b" (třídy typu A a b).  
  
 Pokud jsou oba parametry ukazatele bude čistý porovnání ukazatel adresy a nebude používat převod definovaný uživatelem.  
  
 Následující ukázka generuje C2803:  
  
```  
// C2803.cpp  
// compile with: /c  
class A{};  
bool operator< (const A *left, const A *right);   // C2803  
// try the following line instead  
// bool operator< (const A& left, const A& right);  
```