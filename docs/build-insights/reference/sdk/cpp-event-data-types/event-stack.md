---
title: Třída EventStack
description: C++ Build Insights SDK EventStack odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eaaaedcbf57fdaf8e437a80a7823488febac3e1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324971"
---
# <a name="eventstack-class"></a>Třída EventStack

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `EventStack` je kolekce [Event](event.md) objekty. Všechny události přijaté z c++ sestavení Insights SDK `EventStack` přijít ve formě objektu. Poslední položkou v tomto zásobníku je událost, která je právě zpracovávána. Položky, které předcházejí poslední položce, jsou nadřazenou hierarchií aktuální události. Další informace o modelu událostí používaném v C++ Přehledy sestavení naleznete v [tabulce událostí](../event-table.md).

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

[Zásobník událostí](#event-stack)

### <a name="functions"></a>Functions

[Zadní](#back)
[operátor[]](#subscript-operator)
[Velikost](#size)

## <a name="back"></a><a name="back"></a>Zpět

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>Návratová hodnota

A [RawEvent](raw-event.md) objekt, který představuje poslední položku v zásobníku. Poslední položka v zásobníku událostí je událost, která byla spuštěna.

## <a name="eventstack"></a><a name="event-stack"></a>Zásobník událostí

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>Parametry

*Dat*\
Nezpracovaná data, ze kterého `EventStack` je sestaven.

### <a name="remarks"></a>Poznámky

Obvykle není nutné vytvářet `EventStack` objekty sami. Jsou k dispozici k vám C++ Sestavení Insights SDK při zpracování událostí během analýzy nebo opětovného přihlášení relace.

## <a name="operator"></a><a name="subscript-operator"></a>operátor[]

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>Parametry

*Index*\
Index prvku pro přístup v zásobníku událostí.

### <a name="return-value"></a>Návratová hodnota

A [RawEvent](raw-event.md) objekt, který představuje událost uloženou na pozici označeny *index* v zásobníku událostí.

## <a name="size"></a><a name="size"></a>Velikost

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost zásobníku událostí.

::: moniker-end
