---
title: C3071 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3071
dev_langs:
- C++
helpviewer_keywords:
- C3071
ms.assetid: 69879e66-a60e-4058-9bbd-d5c5e2d8ee37
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 163cb170953c444789e39b906ff4d408739f7514
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3071"></a>C3071 chyby kompilátoru
operátor 'operátor' lze použít pouze na instanci třídy ref nebo typ hodnoty  
  
 Operátor CLR nelze použít v nativním typu. Operátor dají nativní typ například System::Int32 na třídu ref nebo ref struct (typ hodnoty), ale není nativní typu například int nebo alias. Tyto typy nelze do pole z kódu C++ způsobem, který odkazuje na proměnnou nativní proto nelze použít operátor.  
  
 Další informace najdete v tématu [sledování Reference – operátor](../../windows/tracking-reference-operator-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3071.  
  
```  
// C3071.cpp  
// compile with: /clr  
class N {};  
ref struct R {};  
  
int main() {  
   N n;  
   %n;   // C3071  
  
   R r;  
   R ^ r2 = %r;   // OK  
}  
```