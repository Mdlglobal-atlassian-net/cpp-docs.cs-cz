---
title: EventStack – třída
description: Referenční C++ dokumentace třídy EventStack sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6da2fd25082399b82d788c5d119a39e2f7388714
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333403"
---
# <a name="eventstack-class"></a>EventStack – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `EventStack` je kolekcí objektů [událostí](event.md) . Všechny události obdržené ze C++ sady SDK pro Build Insights přicházejí ve formě objektu `EventStack`. Poslední položkou v tomto zásobníku je událost, která se právě zpracovává. Položky, které předcházejí poslední položku, jsou nadřazenou hierarchií aktuální události. Další informace o modelu událostí, který se používá C++ v sestavách pro vytváření sestav, najdete v tématu [tabulka událostí](../event-table.md).

## <a name="syntax"></a>Syntaxe

```cpp
class EventStack
{
public:
    EventStack(const EVENT_COLLECTION_DATA& data);

    size_t      Size() const;
    RawEvent    Back() const;
    RawEvent    operator[] (size_t index) const;
};
```

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

[EventStack](#event-stack)

### <a name="functions"></a>Functions

[Back](#back)
– [operátor []](#subscript-operator)
[Velikost](#size)

## <a name="back"></a>Návrat

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt [RawEvent](raw-event.md) , který představuje poslední položku v zásobníku. Poslední položkou v zásobníku událostí je událost, která se aktivovala.

## <a name="event-stack"></a>EventStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>Parametry

\ *dat*
Nezpracovaná data, ze kterých je sestaven `EventStack`.

### <a name="remarks"></a>Poznámky

Obvykle nemusíte sestavovat `EventStack` objekty sami. Jsou vám k dispozici v C++ sadě SDK pro Build Insights při zpracování událostí během analýzy nebo opětovného protokolování relace.

## <a name="subscript-operator"></a>operator [] – operátor

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>Parametry

\ *indexu*
Index prvku, který má být přístupný v zásobníku událostí.

### <a name="return-value"></a>Návratová hodnota

Objekt [RawEvent](raw-event.md) , který představuje událost uloženou na pozici vyznačenou *indexem* v zásobníku událostí.

## <a name="size"></a>Hodnota

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost zásobníku událostí.

::: moniker-end
