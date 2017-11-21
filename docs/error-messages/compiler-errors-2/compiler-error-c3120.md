---
title: "C3120 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3120
dev_langs: C++
helpviewer_keywords: C3120
ms.assetid: 9b6b210f-9948-4517-a4cc-b4aaadebde68
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6bdd5f5fe41fa794b536f71b3f88db01de99c646
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3120"></a>C3120 chyby kompilátoru
'method_name': metody rozhraní nelze práce se seznamem argumentů proměnných  
  
 Seznam argumentů s proměnnou nelze provést metodu rozhraní. Například následující definice rozhraní generuje C3120:  
  
```  
// C3120.cpp  
__interface A {  
int X(int i, ...);    // C3120  
};  
  
int main(void) { return(0); }  
```