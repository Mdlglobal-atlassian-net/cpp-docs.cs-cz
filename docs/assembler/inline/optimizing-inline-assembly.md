---
title: "Optimalizace vloženého sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e977c89408917643c79f55d415fac212726c50d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="optimizing-inline-assembly"></a>Optimalizace sestavení inline assemblerem
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Přítomnost `__asm` bloku ve funkci ovlivňuje optimalizace několika způsoby. Nejprve není kompilátor zkuste k optimalizaci `__asm` blokovat sám sebe. Zápis v jazyce sestavení je přesně můžete získat. Druhý, přítomnost `__asm` bloku ovlivňuje zaregistrovat proměnné úložiště. Kompilátor zabraňuje enregistering proměnné napříč `__asm` blokování, pokud by byla změněna registrace obsah pomocí `__asm` bloku. Nakonec některé další funkce celou optimalizace nebude mít vliv zahrnutí jazyk sestavení ve funkci.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vložený Assembler](../../assembler/inline/inline-assembler.md)