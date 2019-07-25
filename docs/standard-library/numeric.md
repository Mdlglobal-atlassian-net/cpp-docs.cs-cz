---
title: '&lt;číselné&gt;'
ms.date: 11/04/2016
f1_keywords:
- <numeric>
helpviewer_keywords:
- <numeric> header
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
ms.openlocfilehash: 5862ddd812308c7bf81a5029249caf7e9b4a1168
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453557"
---
# <a name="ltnumericgt"></a>&lt;číselné&gt;

Definuje funkce šablony kontejneru, které provádějí algoritmy numerického zpracování.

## <a name="requirements"></a>Požadavky

**Záhlaví**: \<číselná >

**Obor názvů:** std

## <a name="remarks"></a>Poznámky

Číselné algoritmy připomínají C++ standardní algoritmy knihovny v [ \<algoritmech >](algorithm.md)a můžou pracovat na různých datových strukturách. Patří mezi ně standardní knihovny tříd kontejneru – například [vektory](../standard-library/vector-class.md) a [seznamy](../standard-library/list-class.md)a datové struktury definované programem a pole prvků, které splňují požadavky konkrétního algoritmu. Algoritmy této úrovně obecnosti dosahují přístupem k prvkům kontejneru a jejich přecházením nepřímo prostřednictvím iterátorů. Algoritmy zpracovávají rozsahy iterátoru, které jsou obvykle určeny počáteční a koncovou pozicí. Tyto rozsahy musí být platné v tom smyslu, že na všechny ukazatele v rozsazích musí být možné nepřímo odkazovat a v rámci sekvencí každého rozsahu musí být poslední pozice dosažitelná z první pomocí přírůstku.

Algoritmy rozšíří akce podporované operacemi a členskými funkcemi každého ze C++ standardních kontejnerů knihoven a umožňují interakci s různými typy objektů kontejnerů současně.

## <a name="members"></a>Členové

### <a name="functions"></a>Funkce

|||
|-|-|
|[accumulate](../standard-library/numeric-functions.md#accumulate)|Vypočítá součet všech prvků v určeném rozsahu, včetně některých počátečních hodnot, podle výpočtu po sobě jdoucích částečných součtů nebo vypočítá výsledek po sobě jdoucích částečných výsledků, které jsou získány pomocí zadané binární operace místo operace součtu.|
|[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)|Vypočítá po sobě následující rozdíly mezi každým prvkem a jeho předchůdcem ve vstupním rozsahu a vydá výsledky do cílového rozsahu nebo vypočte výsledek zobecněné procedury, kde je operace rozdílu nahrazena jinou zadanou binární operací.|
|[exclusive_scan](../standard-library/numeric-functions.md#exclusive_scan)||
|[GCD](../standard-library/numeric-functions.md#gcd)||
|[inclusive_scan](../standard-library/numeric-functions.md#inclusive_scan)||
|[inner_product](../standard-library/numeric-functions.md#inner_product)|Vypočítá součet prvků produktu ve dvou rozsazích a přidá jej k zadané počáteční hodnotě nebo vypočítá výsledek zobecněné procedury, kde jsou operace součtu a produktu nahrazeny jinými zadanými binárními operacemi.|
|[iota](../standard-library/numeric-functions.md#iota)|Ukládá počáteční hodnotu počínaje prvním prvkem a naplňuje po sobě jdoucí přírůstky hodnoty (`value++`) v každém elementu v intervalu. `[first, last)`|
|[chyb](../standard-library/numeric-functions.md#lcm)||
|[partial_sum](../standard-library/numeric-functions.md#partial_sum)|Vypočítá sérii součtů ve vstupním rozsahu od prvního prvku *po i*-tý prvek a uloží výsledek každého součtu v *i*-tém prvku cílového rozsahu nebo vypočítá výsledek zobecněné procedury, kde je operace součtu nahradila jinou zadanou binární operací.|
|[úrovně](../standard-library/numeric-functions.md#reduce)||
|[transform_exclusive_scan](../standard-library/numeric-functions.md#transform_exclusive_scan)||
|[transform_inclusive_scan](../standard-library/numeric-functions.md#transform_inclusive_scan)||
|[transform_reduce](../standard-library/numeric-functions.md#transform_reduce)||

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
