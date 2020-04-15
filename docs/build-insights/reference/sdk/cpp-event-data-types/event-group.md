---
title: Třída EventGroup
description: Odkaz na třídu C++ Build Insights SDK EventGroup.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 596c18ca0e9b4d7b26c4ed5209b16871952c4af2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324990"
---
# <a name="eventgroup-class"></a>Třída EventGroup

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Šablona `EventGroup` třídy je základní třída pro všechny třídy zachycení skupiny.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename TActivity>
class EventGroup;
{
public:
    size_t Size() const;

    const TActivity& operator[](size_t index) const;
    const TActivity& Front() const;
    const TActivity& Back() const;

    std::deque<TActivity>::const_iterator begin() const;
    std::deque<TActivity>::const_iterator end() const;
};
```

### <a name="parameters"></a>Parametry

*Aktivita* Typ aktivity obsažený ve skupině.

## <a name="members"></a>Členové

### <a name="functions"></a>Functions

[Konec](#back)
[zadního začátku](#begin)
[end](#end)
[Přední](#front)
[operátor[]](#subscript-operator)
[Velikost](#size)

## <a name="back"></a><a name="back"></a>Zpět

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na poslední událost aktivity ve skupině.

## <a name="begin"></a><a name="begin"></a>Začít

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor ukazující na začátek skupiny událostí aktivity.

## <a name="end"></a><a name="end"></a>Konec

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor ukazující jednu pozici za konec skupiny událostí aktivity.

## <a name="front"></a><a name="front"></a>Přední

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na první událost aktivity ve skupině.

## <a name="operator"></a><a name="subscript-operator"></a>operátor[]

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>Parametry

*Index*\
Index prvku pro přístup ve skupině událostí aktivity.

### <a name="return-value"></a>Návratová hodnota

Událost ze zásobníku událostí uložená na pozici označenou *indexem*.

## <a name="size"></a><a name="size"></a>Velikost

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost skupiny událostí.

::: moniker-end
