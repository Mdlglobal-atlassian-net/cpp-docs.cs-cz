---
title: "Chyba matematické operace M6108 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: M6108
dev_langs: C++
helpviewer_keywords: M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6527a595673fddd9fe320097d093858d1c2c0ca1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="math-error-m6108"></a>Chyba matematické operace M6108
vypočítat druhou odmocninu  
  
 Operand v rámci operace druhou odmocninu bylo záporné.  
  
 Program se ukončí s ukončovacím kódem 136.  
  
> [!NOTE]
>  `sqrt` Funkce běhové knihovny jazyka C a vnitřní funkce FORTRAN **SQRT** nevydávají této chybě. C `sqrt` funkce kontroluje argument před provedením operace a vrací hodnotu chyby, pokud operand je záporná. FORTRAN **SQRT** funkce generuje chyba domény [operace M6201](../../error-messages/tool-errors/math-error-m6201.md) místo této chyby.