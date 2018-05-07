---
title: C3072 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3072
dev_langs:
- C++
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6287ba8e84df96adb0447728dbde8f2031c986cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3072"></a>C3072 chyby kompilátoru
instance třídy ref nelze použít operátor 'operátor'  
  
 použít unární '`operator` ' instance třídy ref převést na typ popisovače – operátor  
  
 Typ CLR vyžaduje CLR operátory, není operátory nativní (nebo standard).  Další informace najdete v tématu [sledování Reference – operátor](../../windows/tracking-reference-operator-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3072.  
  
```  
// C3072.cpp  
// compile with: /clr  
ref class R {};  
  
int main() {  
   R r1;  
   R^ r2 = &r1;   // C3072  
   R^ r3 = %r1;   // OK  
}  
```