---
title: Výhody inline assembleru
ms.date: 08/30/2018
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
ms.openlocfilehash: ecf1598ec90a8600e1fa9aae565724c254dc11e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556738"
---
# <a name="advantages-of-inline-assembly"></a>Výhody inline assembleru

**Specifické pro Microsoft**

Protože vložený assembler nevyžaduje samostatné kroky sestavení a propojení, je pohodlnější než samostatný assembler. Kód vloženého sestavení může použít název proměnné nebo funkce jazyka C, který je v rozsahu, takže jej lze snadno integrovat do kódu jazyka C programu. Protože lze kód sestavení kombinovat s příkazy jazyka C nebo C++ vložené, lze provádět úkoly, které jsou náročné nebo nemožné v jazyce C nebo C++.

Použití sestavení inline assemblerem patří:

- Zápis funkcí v jazyce sestavení.

- Optimalizace místě rychlost důležité části kódu.

- Přístup k hardwaru s přímým přístupem tak pro ovladače zařízení.

- Psaní kódu prologu a epilogu kódu pro "základní" volání.

Vložené sestavení je nástroj pro zvláštní účely. Pokud plánujete přenést aplikaci do různých počítačů, budete pravděpodobně chtít umístit samostatný modul kódu specifické pro počítač. Protože vložený assembler nepodporuje všechna Microsoft Macro Assembler. (MASM) direktivy maker a data, možná bude vhodnější použít MASM pro tyto moduly.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>