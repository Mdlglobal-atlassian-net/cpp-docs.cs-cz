---
title: C3909 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3909
dev_langs:
- C++
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53e89dd422b1289d926ab04a0f17ae4d6185d19d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270814"
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