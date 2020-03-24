---
title: Příkazy iterace (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
ms.openlocfilehash: e8f064fd19e69de2819673f48a7f14e26d60b87e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178250"
---
# <a name="iteration-statements-c"></a>Příkazy iterace (C++)

Příkazy iterace způsobují, že příkazy (nebo složené příkazy) jsou spouštěny nula nebo vícekrát v závislosti na některých kritériích ukončení smyčky. Pokud jsou tyto příkazy složené, jsou spouštěny v pořadí, s výjimkou případů, kdy došlo k příkazu [Break](../cpp/break-statement-cpp.md) nebo [Continue](../cpp/continue-statement-cpp.md) .

C++poskytuje čtyři příkazy iterace – [zatímco](../cpp/while-statement-cpp.md), [do](../cpp/do-while-statement-cpp.md), [pro](../cpp/for-statement-cpp.md)a [rozsah založený na rozsahu](../cpp/range-based-for-statement-cpp.md). Každá z těchto iterací, dokud se výraz ukončení nevyhodnotí jako nula (false), nebo dokud není ukončení smyčky vynuceno pomocí příkazu **Break** . Následující tabulka shrnuje tyto příkazy a jejich akce; jednotlivé oddíly jsou podrobněji popsány v následujících částech.

### <a name="iteration-statements"></a>Příkazy iterace

|Výpis|Vyhodnoceno na|Inicializace|Zvětš|
|---------------|------------------|--------------------|---------------|
|**while**|Horní smyčka|Ne|Ne|
|**do**|Konec smyčky|Ne|Ne|
|**for**|Horní smyčka|Ano|Ano|
|**Rozsah – založený na rozsahu**|Horní smyčka|Ano|Ano|

Část příkazu iterace nemůže být deklarací. Může se ale jednat o složený příkaz obsahující deklaraci.

## <a name="see-also"></a>Viz také

[Přehled příkazů jazyka C++](../cpp/overview-of-cpp-statements.md)
