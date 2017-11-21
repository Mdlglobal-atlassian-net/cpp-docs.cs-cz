---
title: "C2272 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2272
dev_langs: C++
helpviewer_keywords: C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 305b0cd510c088f4731a8430959f76bb57ee33a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2272"></a>C2272 chyby kompilátoru
'function': Modifikátory není povoleno pro statické členské funkce  
  
 A `static` – členská funkce deklarovat s specifikátorem modelu paměti, jako například [const](../../cpp/const-cpp.md) nebo [volatile](../../cpp/volatile-cpp.md), a takové modifikátory nejsou povoleny na `static` členské funkce.  
  
 Následující ukázka generuje C2272:  
  
```  
// C2272.cpp  
// compile with: /c  
class CMyClass {  
public:  
   static void func1() const volatile;   // C2272  func1 is static  
   void func2() const volatile;   // OK  
};  
```