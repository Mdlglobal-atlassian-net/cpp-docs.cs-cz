---
title: Kompilátoru (úroveň 1) upozornění C4550 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4550
dev_langs:
- C++
helpviewer_keywords:
- C4550
ms.assetid: f902b4ed-5f17-48ea-b693-92f4fb8c8054
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d08529006e54427e4327ce96666e551046c07e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276682"
---
# <a name="compiler-warning-level-1-c4550"></a>C4550 kompilátoru upozornění (úroveň 1)
výraz vyhodnocen jako funkci, která chybí seznam argumentů  
  
 Dereferenced ukazatel na funkci chybí seznam argumentů.  
  
## <a name="example"></a>Příklad  
  
```  
// C4550.cpp  
// compile with: /W1  
bool f()  
{  
   return true;  
}  
  
typedef bool (*pf_t)();  
  
int main()  
{  
   pf_t pf = f;  
   if (*pf) {}  // C4550  
   return 0;  
}  
```