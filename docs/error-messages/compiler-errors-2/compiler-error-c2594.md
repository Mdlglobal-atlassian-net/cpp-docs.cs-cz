---
title: C2594 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2594
dev_langs:
- C++
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b1de853b8992d3c02eb94c0b050d72539fc3282
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2594"></a>C2594 chyby kompilátoru
'operátor': nejednoznačné převody z 'type1' na 'type2'  
  
 Žádný převod z *type1* k *type2* byl přímé více než jiný. Dvě možná řešení doporučujeme pro převod z *type1* k *type2*. První možností je definovat přímé převod z *type1* k *type2*, a druhou možností je zadat posloupnost převody z *type1* k  *Type2*.  
  
 Následující ukázka generuje C2594. Navržené řešení do chyba je posloupnost převody:  
  
```  
// C2594.cpp  
// compile with: /c  
struct A{};  
struct I1 : A {};  
struct I2 : A {};  
struct D : I1, I2 {};  
  
A *f (D *p) {  
   return (A*) (p);    // C2594  
  
// try the following line instead  
// return static_cast<A *>(static_cast<I1 *>(p));  
}  
```