---
title: "Kompilátoru (úroveň 1) upozornění C4269 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4269
dev_langs: C++
helpviewer_keywords: C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ee524e998a4d314b7ae3fff74b48b8a6ca6a621f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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