---
title: "C3909 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3909
dev_langs:
- C++
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d22341deb7ef6acd8a93ea234be7231a2c59b96e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3909"></a>C3909 chyby kompilátoru
aWinRT nebo deklaraci spravované události se musí vyskytovat v WinRT nebo spravovaný typ  
  
 V nativním typu byla deklarována na prostředí Windows Runtime událost nebo spravovaný. Pokud chcete vyřešit tuto chybu, deklarujte události v prostředí Windows Runtime nebo spravované typy.  
  
 Další informace najdete v tématu [událostí](../../windows/event-cpp-component-extensions.md).  
  
 Následující ukázka generuje C3909 a ukazuje, jak to opravit:  
  
```  
// C3909.cpp  
// compile with: /clr /c  
delegate void H();  
class X {  
   event H^ E;   // C3909 - use ref class X instead  
};  
  
ref class Y {  
   static event H^ E {  
      void add(H^) {}  
      void remove( H^ h ) {}  
      void raise( ) {}  
   }  
};  
```