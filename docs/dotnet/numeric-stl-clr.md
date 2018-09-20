---
title: číselné (STL/CLR) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/numeric>
- cliext::accumulate
- cliext::adjacent_difference
- cliext::inner_product
- cliext::partial_sum
dev_langs:
- C++
helpviewer_keywords:
- numeric functions [STL/CLR]
- <cliext/numeric> header [STL/CLR]
- <numeric> header [STL/CLR]
- accumulate function [STL/CLR]
- adjacent_difference function [STL/CLR]
- inner_product function [STL/CLR]
- partial_sum function [STL/CLR]
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e5e4a40c42aaf9aa62d8cd14fd1f5dbba784cefa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408179"
---
# <a name="numeric-stlclr"></a>numeric (STL/CLR)

Definuje funkce šablony kontejneru, které provádějí algoritmy numerického zpracování k dispozici.

## <a name="syntax"></a>Syntaxe

```
#include <cliext/numeric>
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext – / číselných >

**Namespace:** cliext –

## <a name="declarations"></a>Deklarace

|Funkce|Popis|
|--------------|-----------------|
|[accumulate (STL/CLR)](#accumulate)|Vypočítá součet všech prvků v zadaném rozsahu, včetně některých počátečních hodnot výpočtem po sobě jdoucích částečných součtů nebo vypočítá výsledek po sobě jdoucích částečných výsledků podobně získaných pomocí zadané binární operace, než součtem.|
|[adjacent_difference (STL/CLR)](#adjacent_difference)|Vypočítá po sobě následující rozdíly mezi každým prvkem a jeho předchůdcem ve vstupním rozsahu a vydá výsledky do cílového rozsahu nebo vypočte výsledek zobecněné procedury, kde je operace rozdílu nahrazena jinou zadanou binární operací.|
|[inner_product (STL/CLR)](#inner_product)|Vypočítá součet prvků produktu ve dvou rozsazích a přidá ji do zadané počáteční hodnotě nebo vypočítá výsledek zobecněné procedury, kde jsou binární operace součtu a produktu nahrazeny jinými zadanými binárními operacemi.|
|[partial_sum (STL/CLR)](#partial_sum)|Vypočítá sérii součtů ve vstupním rozsahu od prvního prvku po `i`tý prvek a uloží výsledek každého součtu v `i`-tém prvku cílového rozsahu nebo vypočítá výsledek zobecněné procedury, kde operace součtu je nahrazena jinou zadanou binární operací.|

## <a name="members"></a>Členové

## <a name="accumulate"></a> accumulate (STL/CLR)

Vypočítá součet všech prvků v zadaném rozsahu, včetně některých počátečních hodnot výpočtem po sobě jdoucích částečných součtů nebo vypočítá výsledek po sobě jdoucích částečných výsledků podobně získaných pomocí zadané binární operace, než součtem.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _Ty> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);
template<class _InIt, class _Ty, class _Fn2> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako číselné funkce standardní knihovny C++ `accumulate`. Další informace najdete v tématu [accumulate](../standard-library/numeric-functions.md#accumulate).

## <a name="adjacent_difference"></a> adjacent_difference (STL/CLR)

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

Tato funkce se chová stejně jako číselné funkce standardní knihovny C++ `adjacent_difference`. Další informace najdete v tématu [adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference).

## <a name="inner_product"></a> inner_product (STL/CLR)

Vypočítá součet prvků produktu ve dvou rozsazích a přidá ji do zadané počáteční hodnotě nebo vypočítá výsledek zobecněné procedury, kde jsou binární operace součtu a produktu nahrazeny jinými zadanými binárními operacemi.

###<a name="syntax"></a>Syntaxe

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

Tato funkce se chová stejně jako číselné funkce standardní knihovny C++ `inner_product`. Další informace najdete v tématu [inner_product](../standard-library/numeric-functions.md#inner_product).

## <a name="partial_sum"></a> partial_sum (STL/CLR)

Vypočítá sérii součtů ve vstupním rozsahu od prvního prvku po `i`tý prvek a uloží výsledek každého součtu v `i`-tém prvku cílového rozsahu nebo vypočítá výsledek zobecněné procedury, kde operace součtu je nahrazena jinou zadanou binární operací.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Poznámky

Tato funkce se chová stejně jako číselné funkce standardní knihovny C++ `partial_sum`. Další informace najdete v tématu [partial_sum](../standard-library/numeric-functions.md#partial_sum).