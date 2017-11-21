---
title: "Kompilátoru (úroveň 1) upozornění C4612 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4612
dev_langs: C++
helpviewer_keywords: C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a2d5ddc76271df594c2bd5b2ae1707933510338
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4612"></a>C4612 kompilátoru upozornění (úroveň 1)
došlo k chybě v patří název souboru  
  
 Toto upozornění se zobrazí s **include_alias – #pragma** Pokud název souboru je nesprávný nebo chybí.  
  
 Argumenty, které mají **include_alias – #pragma** příkaz můžete použít nabídku od (**"***filename***"**) nebo formulář ostré závorky ( **\<**  *filename***>**), ale obě musí používat stejnou formuláře.  
  
## <a name="example"></a>Příklad  
  
```  
// C4612.cpp  
// compile with: /W1 /LD  
#pragma include_alias("StandardIO", <stdio.h>) // C4612  
```