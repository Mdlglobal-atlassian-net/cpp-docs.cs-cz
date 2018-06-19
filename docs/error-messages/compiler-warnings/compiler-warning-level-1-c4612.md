---
title: Kompilátoru (úroveň 1) upozornění C4612 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4612
dev_langs:
- C++
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0983f5d0bb89eaf1daee94468b318557bc83cd05
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281879"
---
# <a name="compiler-warning-level-1-c4612"></a>C4612 kompilátoru upozornění (úroveň 1)
došlo k chybě v patří název souboru  
  
 Toto upozornění se zobrazí s **include_alias – #pragma** Pokud název souboru je nesprávný nebo chybí.  
  
 Argumenty, které mají **include_alias – #pragma** příkaz můžete použít nabídku od (**"***filename***"**) nebo formulář ostré závorky ( **\< ***filename***>**), ale obě musí používat stejnou formuláře.  
  
## <a name="example"></a>Příklad  
  
```  
// C4612.cpp  
// compile with: /W1 /LD  
#pragma include_alias("StandardIO", <stdio.h>) // C4612  
```