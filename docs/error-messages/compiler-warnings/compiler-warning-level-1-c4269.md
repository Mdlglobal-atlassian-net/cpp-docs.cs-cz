---
title: Kompilátoru (úroveň 1) upozornění C4269 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4269
dev_langs:
- C++
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e393c657e12f84d3cadfacd469e35e3472a39d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281788"
---
# <a name="compiler-warning-level-1-c4269"></a>C4269 kompilátoru upozornění (úroveň 1)
"identifikátor": 'const' dat inicializován s kompilátoru generované výchozí konstruktor vytvoří nespolehlivé výsledky  
  
 A **const** automatické instance netriviální třídy je inicializován s generované kompilátorem výchozí konstruktor.  
  
## <a name="example"></a>Příklad  
  
```  
// C4269.cpp  
// compile with: /c /LD /W1  
class X {  
public:  
   int m_data;  
};  
  
void g() {  
   const X x1;   // C4269  
};  
```  
  
 Vzhledem k tomu, že tato instance třídy se vygeneruje v zásobníku, počáteční hodnota `m_data` může být jakýkoli. Protože je také **const** instance, hodnota `m_data` nesmí nikdy změnit.