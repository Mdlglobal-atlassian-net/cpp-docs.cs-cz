---
title: Výhody Inline assembleru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 820c862b90de3fd0d91a68d5a388b77f9a30a142
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682717"
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