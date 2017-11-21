---
title: "C2563 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2563
dev_langs: C++
helpviewer_keywords: C2563
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8fe3ca54a90b91151288076fd657752e3195e318
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2563"></a>C2563 chyby kompilátoru
Neshoda v seznamu formální parametr  
  
 Formální parametr seznam funkci (nebo ukazatel na funkci) neodpovídá těch, které používá jinou funkci (nebo ukazatel na funkci člen). Přiřazení funkcí nebo ukazatele v důsledku toho nelze provést.  
  
 Následující ukázka generuje C2563:  
  
```  
// C2563.cpp  
void func( int );  
void func( int, int );  
int main() {  
   void *fp();  
   fp = func;   // C2563  
}  
```