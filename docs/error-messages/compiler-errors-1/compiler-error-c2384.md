---
title: "C2384 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2384
dev_langs:
- C++
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7494c38c787a0e0877496a8f65556d568d77f7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2384"></a>C2384 chyby kompilátoru
"člen": nelze použít __declspec(thread) členem spravované nebo WinRT – třída  
  
 [Vlákno](../../cpp/thread.md) `__declspec` modifikátor nelze použít na členem spravované nebo prostředí Windows Runtime třídy.  
  
 Statické vláken místní úložiště ve spravovaném kódu lze použít pouze pro staticky načíst knihovny DLL – knihovny DLL musí být staticky načteny při spuštění procesu. Prostředí Windows Runtime nepodporuje místní úložiště vláken.  
  
 Následující řádek vygeneruje C2384 a ukazuje, jak opravit v jazyce C + +/ CLI kódu:  
  
```  
// C2384.cpp  
// compile with: /clr /c  
public ref class B {  
public:  
   __declspec( thread ) static int tls_i = 1;   // C2384  
  
   // OK - declare with attribute instead  
   [System::ThreadStaticAttribute]  
   static int tls_j;  
};  
```