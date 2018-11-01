---
title: __if_not_exists – příkaz
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: d7d172df584200ccc508b281147abf3fa7774952
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629109"
---
# <a name="ifnotexists-statement"></a>__if_not_exists – příkaz

**__If_not_exists** příkaz testuje, jestli existuje zadaný identifikátor. Pokud identifikátor neexistuje, je spuštěn zadaný blok příkazů.

## <a name="syntax"></a>Syntaxe

```
__if_not_exists ( identifier ) { 
statements
};
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*identifikátor*|Identifikátor, jehož existence bude testována.|
|*Příkazy*|Jeden nebo více příkazů, které budou spuštěny, pokud *identifikátor* neexistuje.|

## <a name="remarks"></a>Poznámky

> [!CAUTION]
>  K dosažení nejspolehlivějších výsledků, použít **__if_not_exists** příkaz následujícími omezeními.

- Použít **__if_not_exists** příkazu pouze jednoduché typy, nikoli na šablony.

- Použít **__if_not_exists** příkaz na identifikátory uvnitř i vně třídy. Se nevztahují **__if_not_exists** příkaz pro lokální proměnné.

- Použití **__if_not_exists** příkaz jenom v těle funkce. Mimo tělo funkce **__if_not_exists** příkazu můžete testovat pouze plně definované typy.

- Při testování přetížených funkcí nelze testovat konkrétní formu přetížení.

Doplněk k **__if_not_exists** příkaz je [__if_exists](../cpp/if-exists-statement.md) příkazu.

## <a name="example"></a>Příklad

Příklad použití **__if_not_exists**, naleznete v tématu [__if_exists – příkaz](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Viz také:

[Příkazy výběru](../cpp/selection-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[__if_exists – příkaz](../cpp/if-exists-statement.md)