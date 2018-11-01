---
title: '&lt;Číselné&gt;'
ms.date: 11/04/2016
f1_keywords:
- <numeric>
helpviewer_keywords:
- <numeric> header
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
ms.openlocfilehash: ee93d254dcf49b38cb817ba460060fa72b81e01f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456170"
---
# <a name="ltnumericgt"></a>&lt;Číselné&gt;

Definuje funkce šablony kontejneru, které provádějí algoritmy numerického zpracování.

## <a name="syntax"></a>Syntaxe

```cpp
#include <numeric>
```

## <a name="remarks"></a>Poznámky

Numerické algoritmy se podobají algoritmy standardní knihovny C++ [ \<algoritmus >](algorithm.md)a může pracovat na různých datových strukturách. Mezi ně patří třídy kontejneru standardní knihovny, například [vektoru](../standard-library/vector-class.md) a [seznamu](../standard-library/list-class.md)a programem definované datové struktury a pole prvků, které splňují požadavky konkrétního algoritmu. Algoritmy této úrovně obecnosti dosahují přístupem k prvkům kontejneru a jejich přecházením nepřímo prostřednictvím iterátorů. Algoritmy zpracovávají rozsahy iterátoru, které jsou obvykle určeny počáteční a koncovou pozicí. Tyto rozsahy musí být platné v tom smyslu, že na všechny ukazatele v rozsazích musí být možné nepřímo odkazovat a v rámci sekvencí každého rozsahu musí být poslední pozice dosažitelná z první pomocí přírůstku.

Algoritmy rozšiřují akce podporované operacemi a funkcemi členů každého kontejnery standardní knihovny C++ a umožňují interakci s různými typy objektů kontejnerů ve stejnou dobu.

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[accumulate](../standard-library/numeric-functions.md#accumulate)|Vypočítá součet všech prvků v určeném rozsahu, včetně některých počátečních hodnot, podle výpočtu po sobě jdoucích částečných součtů nebo vypočítá výsledek po sobě jdoucích částečných výsledků, které jsou získány pomocí zadané binární operace místo operace součtu.|
|[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)|Vypočítá po sobě následující rozdíly mezi každým prvkem a jeho předchůdcem ve vstupním rozsahu a vydá výsledky do cílového rozsahu nebo vypočte výsledek zobecněné procedury, kde je operace rozdílu nahrazena jinou zadanou binární operací.|
|[inner_product](../standard-library/numeric-functions.md#inner_product)|Vypočítá součet prvků produktu ve dvou rozsazích a přidá jej k zadané počáteční hodnotě nebo vypočítá výsledek zobecněné procedury, kde jsou operace součtu a produktu nahrazeny jinými zadanými binárními operacemi.|
|[iota](../standard-library/numeric-functions.md#iota)|Obsahuje počáteční hodnotu počínaje prvním prvkem a následně postupné přírůstky hodnoty (`value++`) v každém z prvků intervalu `[first, last)`.|
|[partial_sum](../standard-library/numeric-functions.md#partial_sum)|Vypočítá sérii součtů ve vstupním rozsahu od prvního prvku po *můžu*tý prvek a uloží výsledek každého součtu v *můžu*-tém prvku cílového rozsahu nebo vypočítá výsledek generalizovaný postup, kde operace součtu je nahrazena jinou zadanou binární operací.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
