---
title: Neúplné typy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- void keyword [C], incomplete
- types [C], incomplete
- incomplete types
- unions, incomplete
- arrays [C], incomplete types
- void keyword [C]
- structures, incomplete
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae26bf4f3e036e6e71acc090c174638133d2e881
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759603"
---
# <a name="incomplete-types"></a>Neúplné typy

*Nekompletní typ* je typ, který popisuje identifikátor, ale neobsahuje informace potřebné k určení velikosti identifikátor. Neúplný typ může být:

- Typ struktury, jejíž členy ještě nebyly určeny.

- Typ sjednocení, jehož členy ještě nebyly určeny.

- Typ pole, jehož rozměry ještě nebyly určeny.

**Void** typ je nekompletním typem, který nelze dokončit. Chcete-li dokončit nekompletní typ, zadejte chybějící informace. Následující příklad ukazuje, jak vytvořit a dokončit nekompletní typy.

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