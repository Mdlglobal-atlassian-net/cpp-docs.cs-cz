---
title: Kompilátoru (úroveň 1) upozornění C4799 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4799
dev_langs:
- C++
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f888d6a941ad487ce122e46c43582e1c96525c70
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282935"
---
# <a name="compiler-warning-level-1-c4799"></a>C4799 kompilátoru upozornění (úroveň 1)  
  
> Žádné EMMS na konci funkce '*funkce*.  
  
Funkce má alespoň jeden instrukcí MMX, ale nemá `EMMS` instrukcí. Pokud je použita multimédií instrukce, `EMMS` pokyn nebo `_mm_empty` vnitřní by měla být používána zrušte word multimédií značky na konci MMX kód.  
  
C4799 může dojít, když pomocí ivec.h, která určuje, že kód nepoužívá správně provést instrukci EMMS před vrácením. Toto je false upozornění pro tyto hlavičky. To může vypnout tak, že definujete _SILENCE_IVEC_C4799 v ivec.h. Upozorňujeme však, to také zbaví kompilátor poskytnutí správné upozornění tohoto typu.  
  
Související informace najdete v tématu [nastavit instrukcí MMX společnosti Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).