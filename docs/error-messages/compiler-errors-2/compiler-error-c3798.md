---
title: "C3798 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3798
dev_langs: C++
helpviewer_keywords: C3798
ms.assetid: b2f8b1d8-8812-49b8-a346-28e48f02ba5c
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8841ad9429fb9561952cce1320e030c64eb3a74b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3798"></a>C3798 chyby kompilátoru
'specifikátor': deklarace vlastnosti nemůže mít specifikátor override (musí být umístěny na vlastnost metody get/set místo)  
  
 Vlastnost byla deklarována nesprávně. Další informace naleznete v tématu  
  
-   [Vlastnost](../../windows/property-cpp-component-extensions.md)  
  
-   [abstraktní](../../windows/abstract-cpp-component-extensions.md)  
  
-   [zapečetěná](../../windows/sealed-cpp-component-extensions.md)  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3798  
  
```  
// C3798.cpp  
// compile with: /clr /c  
ref struct A {  
   property int Prop_1 abstract;   // C3798  
   property int Prop_2 sealed;   // C3798  
  
   // OK  
   property int Prop_3 {  
      virtual int get() abstract;  
      virtual void set(int i) abstract;  
   }  
  
   property int Prop_4 {  
      virtual int get() sealed;  
      virtual void set(int i) sealed;  
   }  
};  
```