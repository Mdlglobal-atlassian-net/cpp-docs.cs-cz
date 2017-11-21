---
title: "C2584 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2584
dev_langs: C++
helpviewer_keywords: C2584
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1ff3567f3f4981ecb86926ad76b0d23627da1fb2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2584"></a>C2584 chyby kompilátoru
'Class': přímé základní 'Base2' je nepřístupný; už na základní 'base1 –.  
  
 `Class`již je odvozena přímo z `Base1`. `Base2`také je odvozena z `Base1`. `Class`nelze odvodit z `Base2` protože to znamená (nepřímo), která dědí z `Base1` znovu, což není právní protože `Base1` je již přímé základní třídy.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2584.  
  
```  
// C2584.cpp  
// compile with: /c  
struct A1 {  
   virtual int MyFunction();  
};  
  
struct A2 {  
    virtual int MyFunction();  
};  
  
struct B1: public virtual A1, virtual A2 {  
    virtual int MyFunction();  
};  
  
struct B2: public virtual A2, virtual A1 {  
    virtual int MyFunction();  
};  
  
struct C: virtual B1, B2 {  
    virtual int MyFunction();  
};  
  
struct Z : virtual B2, virtual C {   // C2584  
// try the following line insted  
// struct Z : virtual C {  
    virtual int MyFunction();  
};  
```