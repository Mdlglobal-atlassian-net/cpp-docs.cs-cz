---
title: Ukládání textových literálů
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
ms.openlocfilehash: 0d505479f0844122826a2f07b57eaa69f33932e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157861"
---
# <a name="storage-of-string-literals"></a>Ukládání textových literálů

Znaky textového literálu jsou uloženy v pořadí v oblastech souvislé paměti. Sekvence escape (například ** \\ ** nebo ** \\"**) v rámci řetězcového literálu se počítá jako jeden znak. Znak null (reprezentovaný řídicí sekvencí **\ 0** ) je automaticky připojen k a označuje konec, každý řetězcový literál. (K tomu dochází během [fáze překladu](../preprocessor/phases-of-translation.md) 7.) Všimněte si, že kompilátor nemůže uložit dva identické řetězce na dvou různých adresách. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) vynutí, aby kompilátor umístil jednu kopii stejných řetězců do spustitelného souboru.

## <a name="remarks"></a>Poznámky

**Specifické pro Microsoft**

Řetězce mají statickou dobu ukládání. Informace o době trvání úložiště najdete v tématu [třídy úložiště](../c-language/c-storage-classes.md) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Textové literály jazyka C](../c-language/c-string-literals.md)
