---
title: numeric (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/numeric>
- cliext::accumulate
- cliext::adjacent_difference
- cliext::inner_product
- cliext::partial_sum
helpviewer_keywords:
- numeric functions [STL/CLR]
- <cliext/numeric> header [STL/CLR]
- <numeric> header [STL/CLR]
- accumulate function [STL/CLR]
- adjacent_difference function [STL/CLR]
- inner_product function [STL/CLR]
- partial_sum function [STL/CLR]
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
ms.openlocfilehash: 1939a6dd9b6d8186eb278623f3b0a5a3d851f4d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208478"
---
# <a name="numeric-stlclr"></a>numeric (STL/CLR)

Definuje funkce šablony kontejneru, které provádějí algoritmy poskytované pro číselné zpracování.

## <a name="syntax"></a>Syntaxe

```
#include <cliext/numeric>
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext –/numeric >

**Obor názvů:** cliext –

## <a name="declarations"></a>Deklarace

|Funkce|Popis|
|--------------|-----------------|
|[accumulate (STL/CLR)](#accumulate)|Vypočítá součet všech prvků v zadaném rozsahu včetně některé počáteční hodnoty tím, že provede výpočet po sobě jdoucích částečných součtů nebo vypočítá výsledek následných částečných výsledků podobně jako při použití zadané binární operace, která se liší od součtu.|
|[adjacent_difference (STL/CLR)](#adjacent_difference)|Vypočítá po sobě následující rozdíly mezi každým prvkem a jeho předchůdcem ve vstupním rozsahu a vydá výsledky do cílového rozsahu nebo vypočte výsledek zobecněné procedury, kde je operace rozdílu nahrazena jinou zadanou binární operací.|
|[inner_product (STL/CLR)](#inner_product)|Vypočítá součet elementu v rámci produktu dvou rozsahů a přidá jej k zadané počáteční hodnotě nebo vypočítá výsledek zobecněné procedury, kde jsou souhrn a operace binárního produktu nahrazeny jinými zadanými binárními operacemi.|
|[partial_sum (STL/CLR)](#partial_sum)|Vypočítá sérii součtů ve vstupním rozsahu od prvního prvku po `i`element a ukládá výsledek každého takového součtu v `i`m prvku cílového rozsahu nebo vypočítá výsledek zobecněné procedury, kde je operace součtu nahrazena jinou zadanou binární operací.|

## <a name="members"></a>Členové

## <a name="accumulate-stlclr"></a><a name="accumulate"></a>akumulace (STL/CLR)

Vypočítá součet všech prvků v zadaném rozsahu včetně některé počáteční hodnoty tím, že provede výpočet po sobě jdoucích částečných součtů nebo vypočítá výsledek následných částečných výsledků podobně jako při použití zadané binární operace, která se liší od součtu.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _Ty> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);
template<class _InIt, class _Ty, class _Fn2> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako C++ standardní `accumulate`číselné funkce knihovny. Další informace najdete v tématu [akumulace](../standard-library/numeric-functions.md#accumulate).

## <a name="adjacent_difference-stlclr"></a><a name="adjacent_difference"></a>adjacent_difference (STL/CLR)

Vypočítá po sobě následující rozdíly mezi každým prvkem a jeho předchůdcem ve vstupním rozsahu a vydá výsledky do cílového rozsahu nebo vypočte výsledek zobecněné procedury, kde je operace rozdílu nahrazena jinou zadanou binární operací.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,
        _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako C++ standardní `adjacent_difference`číselné funkce knihovny. Další informace najdete v tématu [adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference).

## <a name="inner_product-stlclr"></a><a name="inner_product"></a>inner_product (STL/CLR)

Vypočítá součet elementu v rámci produktu dvou rozsahů a přidá jej k zadané počáteční hodnotě nebo vypočítá výsledek zobecněné procedury, kde jsou souhrn a operace binárního produktu nahrazeny jinými zadanými binárními operacemi.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2, class _Ty> inline
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Ty _Val);
template<class _InIt1, class _InIt2, class _Ty, class _Fn21,
       class _Fn22> inline
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Ty _Val, _Fn21 _Func1, _Fn22 _Func2);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako C++ standardní `inner_product`číselné funkce knihovny. Další informace najdete v tématu [inner_product](../standard-library/numeric-functions.md#inner_product).

## <a name="partial_sum-stlclr"></a><a name="partial_sum"></a>partial_sum (STL/CLR)

Vypočítá sérii součtů ve vstupním rozsahu od prvního prvku po `i`element a ukládá výsledek každého takového součtu v `i`m prvku cílového rozsahu nebo vypočítá výsledek zobecněné procedury, kde je operace součtu nahrazena jinou zadanou binární operací.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako C++ standardní `partial_sum`číselné funkce knihovny. Další informace najdete v tématu [partial_sum](../standard-library/numeric-functions.md#partial_sum).
