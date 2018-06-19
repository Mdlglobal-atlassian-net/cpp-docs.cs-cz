---
title: Kompilátoru (úroveň 1) upozornění C4190 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4190
dev_langs:
- C++
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e62f6bcfaa499338d5fde1d09cb91574241ce8a0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277891"
---
# <a name="compiler-warning-level-1-c4190"></a>C4190 kompilátoru upozornění (úroveň 1)
'identifier1' má C-propojení zadán, ale vrátí UDT 'identifier2', který není kompatibilní s C  
  
 Funkce nebo ukazatel na funkci má UDT (uživatelem definovaný typ, který je třída, struktura, výčet nebo – typ union) jako návratový typ a `extern` propojení "C". Toto je právní pokud:  
  
-   Všechna volání této funkce dojít z jazyka C++.  
  
-   Definice funkce je v jazyce C++.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// C4190.cpp  
// compile with: /W1 /LD  
struct X  
{  
   int i;  
   X ();  
   virtual ~X ();  
};  
  
extern "C" X func ();   // C4190  
```