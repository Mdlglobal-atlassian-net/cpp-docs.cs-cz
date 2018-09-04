---
title: Optimalizace vloženého sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 49660bdc6d2eb84e6e1bbaeb5ebf0d57e484e9e1
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687873"
---
# <a name="optimizing-inline-assembly"></a>Optimalizace sestavení inline assemblerem

**Specifické pro Microsoft**

Přítomnost `__asm` bloku ve funkci má vliv optimalizace několika způsoby. Nejprve kompilátor nebude pokusu o optimalizaci `__asm` blokovat samotný. Zápis v jazyku sestavení je přesně se zobrazí. Druhý, přítomnost `__asm` bloku ovlivňuje zaregistrovat proměnné úložiště. Kompilátor se vyhnete enregistering proměnné napříč `__asm` blokovat, pokud by se změní obsah do registru `__asm` bloku. Nakonec ovlivní Některé další funkce celou optimalizace zahrnutí jazyk sestavení ve funkci.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>