---
title: C2739 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2739
dev_langs:
- C++
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1448c47ee5f4bdb94cc99e3636b3fcf498ba9f6e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231846"
---
# <a name="compiler-error-c2739"></a>C2739 chyby kompilátoru
"číslo": explicitní spravované nebo WinRT pole dimenze musí být mezi 1 a 32.  
  
 Rozměru pole nebyla mezi 1 a 32.  
  
 Následující ukázka generuje C2739 a ukazuje, jak to opravit:  
  
```  
// C2739.cpp  
// compile with: /clr  
int main() {  
   array<int, -1>^a;   // C2739  
   // try the following line instead  
   // array<int, 2>^a;  
}  
```