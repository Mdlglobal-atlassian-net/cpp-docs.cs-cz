---
title: "C2492 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2492
dev_langs: C++
helpviewer_keywords: C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5410af24b5300b2c03aa0ed4e121abceb6d6d483
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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