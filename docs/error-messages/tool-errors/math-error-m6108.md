---
title: Chyba matematické operace M6108 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6108
dev_langs:
- C++
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4dfeca48aa04ebfbc097649e5c25253166c50dad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="math-error-m6108"></a>Chyba matematické operace M6108
vypočítat druhou odmocninu  
  
 Operand v rámci operace druhou odmocninu bylo záporné.  
  
 Program se ukončí s ukončovacím kódem 136.  
  
> [!NOTE]
>  `sqrt` Funkce běhové knihovny jazyka C a vnitřní funkce FORTRAN **SQRT** nevydávají této chybě. C `sqrt` funkce kontroluje argument před provedením operace a vrací hodnotu chyby, pokud operand je záporná. FORTRAN **SQRT** funkce generuje chyba domény [operace M6201](../../error-messages/tool-errors/math-error-m6201.md) místo této chyby.