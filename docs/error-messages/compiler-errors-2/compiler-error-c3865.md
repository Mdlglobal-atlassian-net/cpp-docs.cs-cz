---
title: "C3865 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3865
dev_langs: C++
helpviewer_keywords: C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: af0873d70fcb4f947e838afba130279edf705ced
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3865"></a>C3865 chyby kompilátoru
'calling_convention': lze použít pouze na nativní členské funkce  
  
 Konvence volání byl použit na funkci, která se globální funkce nebo na spravované – členská funkce. Konvence volání lze použít pouze v nativní (není spravované) členské funkce.  
  
 Další informace najdete v tématu [konvence volání](../../cpp/calling-conventions.md).  
  
 Následující ukázka generuje C3865:  
  
```  
// C3865.cpp  
// compile with: /clr  
// processor: x86  
void __thiscall Func(){}   // C3865  
  
// OK  
struct MyType {  
   void __thiscall Func(){}  
};  
```