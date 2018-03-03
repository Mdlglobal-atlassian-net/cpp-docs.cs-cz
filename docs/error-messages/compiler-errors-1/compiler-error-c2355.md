---
title: "C2355 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2355
dev_langs:
- C++
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3060f97645061e0244091b416dcdfeef343f90b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2355"></a>C2355 chyby kompilátoru
'this': může být odkazováno pouze uvnitř nestatické členské funkce nebo data nestatické členské inicializátory  
  
 `this` Ukazatel je platná pouze v rámci nestatické členské funkce nebo data nestatické členské inicializátory. K této chybě může dojít při oboru – třída definice členské funkce mimo deklaraci třídy není kvalifikován správně. Chyba může také nastat, když `this` ukazatele se používá ve funkci, která není deklarován v třídě.  
  
 Chcete-li tento problém vyřešit, ujistěte se, definice členské funkce odpovídá deklaraci členské funkce ve třídě, a že není deklarovaný statické. Pro data člena inicializátory zkontrolujte, zda že datový člen není deklarovaný statické.  
  
 Následující ukázka generuje C2355 a ukazuje, jak to opravit:  
  
```  
// C2355.cpp  
// compile with: /c  
class MyClass {};  
MyClass *p = this;   // C2355  
  
// OK  
class MyClass2 {  
public:  
   void Test() {  
      MyClass2 *p = this;  
   }  
};  
```