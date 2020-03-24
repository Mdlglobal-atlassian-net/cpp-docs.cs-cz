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
ms.openlocfilehash: 0051b16ddc19e233cfac2688c0b77e1e023f0833
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169263"
---
# <a name="optimizing-inline-assembly"></a>Optimalizace sestavení inline assemblerem

**Specifické pro společnost Microsoft**

Přítomnost `__asm`ového bloku ve funkci má vliv na optimalizaci několika způsoby. Za prvé se kompilátor nepokouší optimalizovat `__asm` samotný blok. To, co napíšete do jazyka sestavení, je přesně to, co dostanete. Za druhé, přítomnost `__asm`ho bloku má vliv na úložiště proměnné registru. Kompilátor zabraňuje proměnným zaregistrování napříč blokem `__asm`, pokud by obsah registru byl změněn pomocí bloku `__asm`. Nakonec budou některé další optimalizace na úrovni funkcí ovlivněny zahrnutím jazyka sestavení ve funkci.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>
