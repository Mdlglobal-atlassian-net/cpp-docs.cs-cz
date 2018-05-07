---
title: C3908 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3908
dev_langs:
- C++
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f971ec355c3f1c3772b2a0cd4059cf0a8abd630
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3908"></a>C3908 chyby kompilátoru
úroveň přístupu je méně omezující než 'konstrukce.  
  
 Metodu přistupujícího objektu vlastnosti (get nebo sadu) nemůže mít méně omezující přístup, než je zadaná v samotné vlastnosti přístup.  Stejně tak v případě metody přístupových objektů události.  
  
 Další informace najdete v tématu [vlastnost](../../windows/property-cpp-component-extensions.md) a [událostí](../../windows/event-cpp-component-extensions.md).  
  
 Následující ukázka generuje C3908:  
  
```  
// C3908.cpp  
// compile with: /clr  
ref class X {  
protected:  
   property int i {  
   public:   // C3908 property i is protected   
      int get();  
   private:  
      void set(int);   // OK more restrictive  
   };  
};  
```