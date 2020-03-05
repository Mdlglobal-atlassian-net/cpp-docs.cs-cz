---
title: FrontEndFile – třída
description: Referenční C++ dokumentace třídy FrontEndFile sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFile
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 094b1326765e0e8edb00534ecb3d94c46702d4ec
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333284"
---
# <a name="frontendfile-class"></a>FrontEndFile – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `FrontEndFile` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [FRONT_END_FILE](../event-table.md#front-end-file) události.

## <a name="syntax"></a>Syntaxe

```cpp
class FrontEndFile : public Activity
{
public:
    FrontEndFile(const RawEvent& event);

    const char* Path() const;
};
```

## <a name="members"></a>Členové

Spolu se zděděnými členy ze své základní třídy [aktivity](activity.md) obsahuje Třída `FrontEndFile` následující členy:

### <a name="constructors"></a>Konstruktory

[FrontEndFile](#front-end-file)

### <a name="functions"></a>Functions

[Cesta](#path)

## <a name="front-end-file"></a>FrontEndFile

```cpp
FrontEndFile(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [FRONT_END_FILE](../event-table.md#front-end-file) .

## <a name="path"></a>Dílčí

```cpp
const char* Path() const;
```

### <a name="return-value"></a>Návratová hodnota

Absolutní cesta k souboru kódovaná v kódování UTF-8.

::: moniker-end
