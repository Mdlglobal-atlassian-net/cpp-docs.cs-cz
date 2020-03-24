---
title: Výhody inline assembleru
ms.date: 08/30/2018
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
ms.openlocfilehash: 7e634f78eca753487cf122ac95df55828bb64625
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169653"
---
# <a name="advantages-of-inline-assembly"></a>Výhody inline assembleru

**Specifické pro společnost Microsoft**

Protože vložený assembler nevyžaduje samostatné kroky sestavení a propojení, je pohodlnější než samostatný assembler. Kód vloženého sestavení může použít název proměnné nebo funkce jazyka C, který je v rozsahu, takže jej lze snadno integrovat do kódu jazyka C programu. Vzhledem k tomu, že kód sestavení může být smíšeně C++ vložen s c nebo příkazy, může provádět úkoly, které jsou v jazyce C++c nenáročné nebo nemožné.

Použití vloženého sestavení zahrnuje:

- Psaní funkcí v jazyce sestavení.

- Přímá optimalizace důležitých částí kódu.

- Umožnění přímého hardwarového přístupu pro ovladače zařízení.

- Zápis kódu prologu a epilogu pro volání typu "holé".

Vložené sestavení je nástroj pro speciální účely. Pokud plánujete port aplikace na jiné počítače, pravděpodobně budete chtít kód specifický pro konkrétní počítač umístit do samostatného modulu. Vzhledem k tomu, že Inline assembler nepodporuje všechna makra a direktivy dat assembleru (MASM) společnosti Microsoft, může být vhodnější použít pro tyto moduly MASM.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>
