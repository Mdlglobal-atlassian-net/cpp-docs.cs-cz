---
title: Neúplné typy
ms.date: 11/04/2016
helpviewer_keywords:
- void keyword [C], incomplete
- types [C], incomplete
- incomplete types
- unions, incomplete
- arrays [C], incomplete types
- void keyword [C]
- structures, incomplete
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
ms.openlocfilehash: e7a5cd7624b55e7bce0fbd09451ab42426f5bc37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232889"
---
# <a name="incomplete-types"></a>Neúplné typy

*Neúplný typ* je typ, který popisuje identifikátor, ale neobsahuje informace potřebné k určení velikosti identifikátoru. Neúplný typ může být:

- Typ struktury, jejíž členy ještě nebyly určeny.

- Typ sjednocení, jehož členy ještě nebyly určeny.

- Typ pole, jehož rozměry ještě nebyly určeny.

Typ **void** je nekompletní typ, který nelze dokončit. Chcete-li dokončit nekompletní typ, zadejte chybějící informace. Následující příklad ukazuje, jak vytvořit a dokončit nekompletní typy.

- Chcete-li vytvořit nekompletní typ struktury, deklarujte typ struktury bez zadání jejích členů. V tomto příkladu ukazatel `ps` ukazuje na nekompletní typ struktury s názvem `student`.

    ```C
    struct student *ps;
    ```

- Chcete-li dokončit nekompletní typ struktury, deklarujte dále ve stejném oboru stejný typ struktury se zadanými členy, například

    ```C
    struct student
    {
        int num;
    }                   /* student structure now completed */
    ```

- Chcete-li vytvořit nekompletní typ pole, deklarujte typ pole bez určení počtu opakování. Příklad:

    ```C
    char a[];  /* a has incomplete type */
    ```

- Chcete-li dokončit nekompletní typ pole, deklarujte stejný název dále ve stejném oboru se zadaným počtem opakování, například

    ```C
    char a[25]; /* a now has complete type */
    ```

## <a name="see-also"></a>Viz také

[Deklarace a typy](../c-language/declarations-and-types.md)
