---
title: "C3908 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3908
dev_langs: C++
helpviewer_keywords: C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 05b4f772c5c1acf8da9247f27fa92a947a0ffc5b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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