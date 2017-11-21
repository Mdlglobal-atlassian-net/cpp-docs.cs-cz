---
title: "C2491 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2491
dev_langs: C++
helpviewer_keywords: C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 83b369d72b4d2ed296f6abeb68cc69b8c233326e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2491"></a>C2491 chyby kompilátoru
"identifikátor": definice funkce dllimport není povoleno  
  
 Datové členy statických dat a funkce lze deklarovat jako `dllimport`s, ale není definováno jako `dllimport`s.  
  
 Chcete-li tento problém vyřešit, odeberte `__declspec(dllimport)` specifikátor z definice funkce.  
  
 Následující ukázka generuje C2491:  
  
```  
// C2491.cpp  
// compile with: /c  
// function definition  
void __declspec(dllimport) funcB() {}   // C2491  
  
// function declaration  
void __declspec(dllimport) funcB();   // OK  
```