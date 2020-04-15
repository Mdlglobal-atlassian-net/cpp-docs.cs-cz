---
title: __if_not_exists – příkaz
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 1118f9fcca525b2b2d5869fb507ee974d2b0d28f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374144"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists – příkaz

Příkaz **__if_not_exists** testuje, zda zadaný identifikátor existuje. Pokud identifikátor neexistuje, je spuštěn zadaný blok příkazů.

## <a name="syntax"></a>Syntaxe

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Identifikátor*|Identifikátor, jehož existence bude testována.|
|*Příkazy*|Jeden nebo více příkazů, které mají být provedeny, pokud *identifikátor* neexistuje.|

## <a name="remarks"></a>Poznámky

> [!CAUTION]
> Chcete-li dosáhnout nejspolehlivějších výsledků, použijte **příkaz __if_not_exists** pod následujícími omezeními.

- Použijte **příkaz __if_not_exists** pouze na jednoduché typy, nikoli na šablony.

- Použijte **příkaz __if_not_exists** na identifikátory uvnitř i vně třídy. Nepoužívejte **příkaz __if_not_exists** na místní proměnné.

- Příkaz **__if_not_exists** použijte pouze v těle funkce. Mimo tělo funkce, příkaz **__if_not_exists** může testovat pouze plně definované typy.

- Při testování přetížených funkcí nelze testovat konkrétní formu přetížení.

Doplňkem **prohlášení __if_not_exists** je [prohlášení __if_exists.](../cpp/if-exists-statement.md)

## <a name="example"></a>Příklad

Příklad použití **__if_not_exists**naleznete v [tématu __if_exists Prohlášení](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Viz také

[Příkazy výběru](../cpp/selection-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[__if_exists – příkaz](../cpp/if-exists-statement.md)
