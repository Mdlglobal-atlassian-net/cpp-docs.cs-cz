---
title: Objekt EnvironmentVariable – třída
description: Referenční C++ dokumentace třídy objekt EnvironmentVariable sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 19e9278e76fb2116dac30a0e790fba86c6c56484
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333438"
---
# <a name="environmentvariable-class"></a>Objekt EnvironmentVariable – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `EnvironmentVariable` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) události.

## <a name="syntax"></a>Syntaxe

```cpp
class EnvironmentVariable : public SimpleEvent
{
public:
    EnvironmentVariable(const RawEvent& event);

    const wchar_t* Name() const;
    const wchar_t* Value() const;
};
```

## <a name="members"></a>Členové

Společně s děděnými členy ze své základní třídy [SimpleEvent](simple-event.md) obsahuje Třída `EnvironmentVariable` následující členy:

### <a name="constructors"></a>Konstruktory

[Objekt EnvironmentVariable](#environment-variable)

### <a name="functions"></a>Functions

[Název](#name)
[hodnota](#value)

## <a name="environment-variable"></a>Objekt EnvironmentVariable

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) .

## <a name="name"></a>Jméno

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>Návratová hodnota

Název proměnné prostředí

## <a name="value"></a>Osa

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota proměnné prostředí.

::: moniker-end
