---
title: Ukládání textových literálů
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
ms.openlocfilehash: b6c266c1381cc7f4e505916a916f5a924a626792
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481221"
---
# <a name="storage-of-string-literals"></a>Ukládání textových literálů

Znaky textového literálu jsou uloženy v pořadí v oblastech souvislé paměti. Řídicí sekvence (jako například **\\ \\** nebo  **\\"**) v rámci textového literálu počítá jako jeden znak. Znak null (reprezentovaný **\0** sekvence escape) se automaticky připojí a označí konce každého řetězce literálu. (K tomu dochází během [fáze překladu](../preprocessor/phases-of-translation.md) 7.) Všimněte si, že kompilátor nesmí uložit dva shodné řetězce na dvě různá místa. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) vynutí, aby kompilátor umístí jednu kopii shodného řetězce do spustitelného souboru.

## <a name="remarks"></a>Poznámky

**Specifické pro Microsoft**

Řetězce mají statickou dobu ukládání. Zobrazit [třídy úložiště](../c-language/c-storage-classes.md) informace o dobou trvání úložiště.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Textové literály jazyka C](../c-language/c-string-literals.md)