---
title: Ukládání textových literálů
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
ms.openlocfilehash: 0d505479f0844122826a2f07b57eaa69f33932e8
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148124"
---
# <a name="storage-of-string-literals"></a>Ukládání textových literálů

Znaky textového literálu jsou uloženy v pořadí v oblastech souvislé paměti. Řídicí sekvence (jako například **\\ \\** nebo  **\\"**) v rámci textového literálu počítá jako jeden znak. Znak null (reprezentovaný **\0** sekvence escape) se automaticky připojí a označí konce každého řetězce literálu. (K tomu dochází během [fáze překladu](../preprocessor/phases-of-translation.md) 7.) Všimněte si, že kompilátor nesmí uložit dva shodné řetězce na dvě různá místa. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) vynutí, aby kompilátor umístí jednu kopii shodného řetězce do spustitelného souboru.

## <a name="remarks"></a>Poznámky

**Microsoft Specific**

Řetězce mají statickou dobu ukládání. Zobrazit [třídy úložiště](../c-language/c-storage-classes.md) informace o dobou trvání úložiště.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Textové literály jazyka C](../c-language/c-string-literals.md)
