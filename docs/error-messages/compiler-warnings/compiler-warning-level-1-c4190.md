---
title: "Kompilátoru (úroveň 1) upozornění C4190 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4190
dev_langs: C++
helpviewer_keywords: C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 127eb4327826412d605f2a4a008e411880998073
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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