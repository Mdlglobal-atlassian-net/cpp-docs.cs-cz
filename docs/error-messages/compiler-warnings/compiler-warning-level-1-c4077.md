---
title: "Kompilátoru (úroveň 1) upozornění C4077 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4077
dev_langs: C++
helpviewer_keywords: C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2301e1ee077adee35706a4f80d8b2a738743851e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4077"></a>C4077 kompilátoru upozornění (úroveň 1)
Neznámý check_stack – možnost  
  
 Původní formu **check_stack –** – Direktiva pragma se používá s argumentem neznámé. Argument musí být `+`, `-`, `(on)`, `(off)`, nebo je prázdný.  
  
 Kompilátor ignoruje – Direktiva pragma a kontrola ověření zásobníku zůstane beze změny.  
  
## <a name="example"></a>Příklad  
  
```  
// C4077.cpp  
// compile with: /W1 /LD  
#pragma check_stack yes // C4077  
#pragma check_stack +    // Correct old form  
#pragma check_stack (on) // Correct new form  
```