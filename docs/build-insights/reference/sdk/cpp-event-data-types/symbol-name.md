---
title: Symbol – třída
description: Referenční C++ dokumentace třídy symbol sestavení sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b5e9a9b22db99c099b9f7dc1813fb335358a83e8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332997"
---
# <a name="symbolname-class"></a>Symbol – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `SymbolName` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [SYMBOL_NAME](../event-table.md#symbol-name) události.

## <a name="syntax"></a>Syntaxe

```cpp
class SymbolName : public SimpleEvent
{
public:
    SymbolName(const RawEvent& event);

    const unsigned long long&  Key() const;
    const char*                Name() const;
};
```

## <a name="members"></a>Členové

Společně s děděnými členy ze své základní třídy [SimpleEvent](simple-event.md) obsahuje Třída `SymbolName` následující členy:

### <a name="constructors"></a>Konstruktory

[Symbol označení](#symbol-name)

### <a name="functions"></a>Functions

[Název](#name)
[klíče](#key)

## <a name="key"></a>Zkrat

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>Návratová hodnota

Číselný identifikátor typu reprezentovaného tímto symbolem. Tento identifikátor je jedinečný v rámci front-endového průchodu kompilátoru.

## <a name="name"></a>Jméno

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Návratová hodnota

Název typu reprezentovaného symbolem kódovaný v kódování UTF-8.

## <a name="symbol-name"></a>Symbol označení

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [SYMBOL_NAME](../event-table.md#symbol-name) .

::: moniker-end
