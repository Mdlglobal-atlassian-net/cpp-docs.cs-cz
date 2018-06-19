---
title: C2492 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2492
dev_langs:
- C++
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68b3d769c5b86be172a0a27828fb1dc3905959d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197361"
---
# <a name="compiler-error-c2492"></a>C2492 chyby kompilátoru
'*proměnná*': data s trvání uložení vlákno nemusí mít rozhraní knihovny dll    
  
 Proměnná je deklarovaný s [vlákno](../../cpp/thread.md) atribut a s knihovnou DLL rozhraní. Na adresu `thread` proměnné není znám, dokud běhu, takže ji nelze ho propojit s knihovny DLL import nebo export.  
  
 Následující ukázka generuje C2492:  
  
```  
// C2492.cpp  
// compile with: /c  
class C {  
public:  
   char   ch;  
};  
  
__declspec(dllexport) __declspec(thread) C c_1;   // C2492  
__declspec(thread) C c_1;   // OK  
```