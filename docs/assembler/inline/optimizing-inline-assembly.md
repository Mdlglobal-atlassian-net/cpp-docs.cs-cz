---
title: Optimalizace vloženého sestavení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c494594e3b7c541487f34fd33359b0e31f73dd61
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050555"
---
# <a name="optimizing-inline-assembly"></a>Optimalizace sestavení inline assemblerem
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Přítomnost `__asm` bloku ve funkci ovlivňuje optimalizace několika způsoby. Nejprve není kompilátor zkuste k optimalizaci `__asm` blokovat sám sebe. Zápis v jazyce sestavení je přesně můžete získat. Druhý, přítomnost `__asm` bloku ovlivňuje zaregistrovat proměnné úložiště. Kompilátor zabraňuje enregistering proměnné napříč `__asm` blokování, pokud by byla změněna registrace obsah pomocí `__asm` bloku. Nakonec některé další funkce celou optimalizace nebude mít vliv zahrnutí jazyk sestavení ve funkci.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vkládaný assembler](../../assembler/inline/inline-assembler.md)