---
title: C3181 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3181
dev_langs:
- C++
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33d5c42ce7fec65b2b4481b46590396f3af7d97a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252160"
---
# <a name="compiler-error-c3181"></a>C3181 chyby kompilátoru
'type': Neplatný operand operátoru  
  
Byl předán neplatný parametr [typeid](../../windows/typeid-cpp-component-extensions.md) operátor. Parametr musí být spravovaného typu.  
  
Všimněte si, že kompilátor používá aliasy pro nativní typy, které jsou mapovány na typy v modulu CLR.  
  
Následující ukázka generuje C3181:  
  
```  
// C3181a.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181  
   Type ^pType2 = int::typeid;   // OK  
}  
```  
