---
title: ForceInlinee – třída
description: Referenční C++ dokumentace třídy ForceInlinee sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7d3cce13601a0b3edbcd2b57664b2d0d94a7d3df
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333333"
---
# <a name="forceinlinee-class"></a>ForceInlinee – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `ForceInlinee` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [FORCE_INLINEE](../event-table.md#force-inlinee) události.

## <a name="syntax"></a>Syntaxe

```cpp
class ForceInlinee : public SimpleEvent
{
public:
    ForceInlinee(const RawEvent& event);

    const char*             Name() const;
    const unsigned short&   Size() const;
};
```

## <a name="members"></a>Členové

Společně s děděnými členy ze své základní třídy [SimpleEvent](simple-event.md) obsahuje Třída `ForceInlinee` následující členy:

### <a name="constructors"></a>Konstruktory

[ForceInlinee](#force-inlinee)

### <a name="functions"></a>Functions

[Název](#name)
[Velikost](#size)

## <a name="force-inlinee"></a>ForceInlinee

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [FORCE_INLINEE](../event-table.md#force-inlinee) .

## <a name="name"></a>Jméno

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Návratová hodnota

Název vysílané vložené funkce kódované v kódování UTF-8.

## <a name="size"></a>Hodnota

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost vynuceně vložené funkce jako počet zprostředkujících instrukcí.

::: moniker-end
