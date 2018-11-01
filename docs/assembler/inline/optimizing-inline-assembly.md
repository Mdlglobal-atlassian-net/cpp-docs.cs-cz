---
title: Optimalizace sestavení inline assemblerem
ms.date: 08/30/2018
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
ms.openlocfilehash: d4956ba12e0bc268d78a895e6cb1ec6e2059262a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538863"
---
# <a name="optimizing-inline-assembly"></a>Optimalizace sestavení inline assemblerem

**Specifické pro Microsoft**

Přítomnost `__asm` bloku ve funkci má vliv optimalizace několika způsoby. Nejprve kompilátor nebude pokusu o optimalizaci `__asm` blokovat samotný. Zápis v jazyku sestavení je přesně se zobrazí. Druhý, přítomnost `__asm` bloku ovlivňuje zaregistrovat proměnné úložiště. Kompilátor se vyhnete enregistering proměnné napříč `__asm` blokovat, pokud by se změní obsah do registru `__asm` bloku. Nakonec ovlivní Některé další funkce celou optimalizace zahrnutí jazyk sestavení ve funkci.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>