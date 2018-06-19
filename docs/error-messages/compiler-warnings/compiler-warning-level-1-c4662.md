---
title: Kompilátoru (úroveň 1) upozornění C4662 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4662
dev_langs:
- C++
helpviewer_keywords:
- C4662
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60739959a6c26e0a1674b287ebf0a4605966e09b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283423"
---
# <a name="compiler-warning-level-1-c4662"></a>C4662 kompilátoru upozornění (úroveň 1)
Explicitní vytvoření instance; šablony třídy 'identifier1' neobsahuje žádnou definici ze kterého se specializují 'identifier2.  
  
 Pro zadanou třídu šablony byla deklarována, ale není definován.  
  
## <a name="example"></a>Příklad  
  
```  
// C4662.cpp  
// compile with: /W1 /LD  
template<class T, int i> class MyClass; // no definition  
template MyClass< int, 1>;              // C4662  
```