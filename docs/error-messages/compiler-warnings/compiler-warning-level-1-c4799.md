---
title: "Kompilátoru (úroveň 1) upozornění C4799 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4799
dev_langs: C++
helpviewer_keywords: C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6b73cd3ee4fd530618179f05b5ab22fe8b29346f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4799"></a>C4799 kompilátoru upozornění (úroveň 1)  
  
> Žádné EMMS na konci funkce '*funkce*.  
  
Funkce má alespoň jeden instrukcí MMX, ale nemá `EMMS` instrukcí. Pokud je použita multimédií instrukce, `EMMS` pokyn nebo `_mm_empty` vnitřní by měla být používána zrušte word multimédií značky na konci MMX kód.  
  
C4799 může dojít, když pomocí ivec.h, která určuje, že kód nepoužívá správně provést instrukci EMMS před vrácením. Toto je false upozornění pro tyto hlavičky. To může vypnout tak, že definujete _SILENCE_IVEC_C4799 v ivec.h. Upozorňujeme však, to také zbaví kompilátor poskytnutí správné upozornění tohoto typu.  
  
Související informace najdete v tématu [nastavit instrukcí MMX společnosti Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).