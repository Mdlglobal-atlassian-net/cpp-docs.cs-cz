---
title: "C3254 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3254
dev_langs:
- C++
helpviewer_keywords:
- C3254
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7fea1dce2c872b1ab472c228f64d5937b81f9943
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3254"></a>C3254 chyby kompilátoru
'explicitní override': třída obsahuje explicitní přepsání přepsat, ale není odvozen z rozhraní, které obsahuje deklarace funkce  
  
 Pokud jste [explicitně přepsat](../../cpp/explicit-overrides-cpp.md) metodu, třídu, která obsahuje přepsání musí být odvozeny, přímo ani nepřímo, z typ, který obsahuje funkci přepíšete.  
  
 Následující ukázka generuje C3254:  
  
```  
// C3254.cpp  
__interface I  
{  
   void f();  
};  
  
__interface I1 : I  
{  
};  
  
struct A /* : I1 */  
{  
   void I1::f()  
   {   // C3254, uncomment : I1 to resolve this C3254  
   }  
};  
  
int main()  
{  
}  
```