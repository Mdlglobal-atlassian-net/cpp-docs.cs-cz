---
title: "C2270 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2270
dev_langs: C++
helpviewer_keywords: C2270
ms.assetid: b52c068e-0b61-42e7-b775-4d57b3ddcba0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bc380d8a44e61ac0f709b8440d788d12f3795922
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2270"></a>C2270 chyby kompilátoru
'function': Modifikátory není povoleno na nečlenský funkce  
  
 Funkce nečlenský je deklarovaný s [const](../../cpp/const-cpp.md), [volatile](../../cpp/volatile-cpp.md), nebo jiné modifikátor modelu paměti.  
  
 Následující ukázka generuje C2270:  
  
```  
// C2270.cpp  
// compile with: /c  
void func1(void) const;   // C2270, nonmember function  
  
void func2(void);  
  
class CMyClass {  
public:  
   void func2(void) const;  
};  
```