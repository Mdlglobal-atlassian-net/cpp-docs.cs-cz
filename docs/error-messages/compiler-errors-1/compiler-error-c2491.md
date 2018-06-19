---
title: C2491 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2491
dev_langs:
- C++
helpviewer_keywords:
- C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e46d63f6602af7fe962f8b139c93a4b9a561783
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198882"
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