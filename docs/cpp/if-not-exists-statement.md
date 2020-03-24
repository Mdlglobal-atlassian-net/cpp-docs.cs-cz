---
title: __if_not_exists – příkaz
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 7372ac127a7b4dd5c05d58cfecca25f87690b0ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178174"
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
|*RID*|Identifikátor, jehož existence bude testována.|
|*učiněn*|Jeden nebo více příkazů, které se mají provést, pokud *identifikátor* neexistuje.|

## <a name="remarks"></a>Poznámky

> [!CAUTION]
>  Chcete-li dosáhnout nejspolehlivějších výsledků, použijte příkaz **__if_not_exists** v následujících omezeních.

- Použijte příkaz **__if_not_exists** pouze na jednoduché typy, nikoli na šablony.

- Použijte příkaz **__if_not_exists** pro identifikátory uvnitř nebo vně třídy. Neaplikujte příkaz **__if_not_exists** na lokální proměnné.

- Použijte příkaz **__if_not_exists** pouze v těle funkce. Mimo tělo funkce může příkaz **__if_not_exists** testovat pouze plně definované typy.

- Při testování přetížených funkcí nelze testovat konkrétní formu přetížení.

Příplatek k příkazu **__if_not_exists** je příkaz [__if_exists](../cpp/if-exists-statement.md) .

## <a name="example"></a>Příklad

Příklad použití **__if_not_exists**naleznete v tématu [__if_exists příkaz](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Viz také

[Příkazy výběru](../cpp/selection-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[__if_exists – příkaz](../cpp/if-exists-statement.md)
