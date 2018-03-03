---
title: "Optimalizace vloženého sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 21f6954ece6adcc60fbb3a8620dd427e7c21042a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="optimizing-inline-assembly"></a>Optimalizace sestavení inline assemblerem
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Přítomnost `__asm` bloku ve funkci ovlivňuje optimalizace několika způsoby. Nejprve není kompilátor zkuste k optimalizaci `__asm` blokovat sám sebe. Zápis v jazyce sestavení je přesně můžete získat. Druhý, přítomnost `__asm` bloku ovlivňuje zaregistrovat proměnné úložiště. Kompilátor zabraňuje enregistering proměnné napříč `__asm` blokování, pokud by byla změněna registrace obsah pomocí `__asm` bloku. Nakonec některé další funkce celou optimalizace nebude mít vliv zahrnutí jazyk sestavení ve funkci.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vkládaný assembler](../../assembler/inline/inline-assembler.md)