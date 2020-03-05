---
title: Event – třída
description: Referenční C++ dokumentace třídy Event Insights sady SDK pro sestavování
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ac8ac70f3fc160714b86dd0c483808a4d06e7699
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333431"
---
# <a name="eventgroup-class"></a>Event – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Šablona třídy `EventGroup` je základní třídou pro všechny třídy zachycení skupiny.

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

*TActivity* Typ aktivity obsažený ve skupině.

## <a name="members"></a>Členové

### <a name="functions"></a>Functions

[Zpět](#back)
[začínat](#begin)
[End](#end)
[přední](#front)
[operator []](#subscript-operator)
[velikosti](#size)

## <a name="back"></a>Návrat

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na událost poslední aktivita ve skupině.

## <a name="begin"></a>ifunctiondiscovery

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor ukazující na začátek skupiny událostí aktivity.

## <a name="end"></a>účelu

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor ukazující jednu pozici za konec skupiny událostí aktivity.

## <a name="front"></a>Dopředu

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na první událost aktivity ve skupině.

## <a name="subscript-operator"></a>operator [] – operátor

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>Parametry

\ *indexu*
Index prvku, ke kterému má být přístup ve skupině událostí aktivity.

### <a name="return-value"></a>Návratová hodnota

Událost z zásobníku událostí uložená na pozici vyznačenou *indexem*

## <a name="size"></a>Hodnota

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost skupiny událostí.

::: moniker-end
