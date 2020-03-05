---
title: CompilerPass – třída
description: Referenční C++ dokumentace třídy CompilerPass sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c2fa1c2c4be8aaf5bec77b383f93a4b033ca8e3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333473"
---
# <a name="compilerpass-class"></a>CompilerPass – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `CompilerPass` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [BACK_END_PASS](../event-table.md#back-end-pass) nebo [FRONT_END_PASS](../event-table.md#front-end-pass) události.

## <a name="syntax"></a>Syntaxe

```cpp
class CompilerPass : public Activity
{
public:
    enum class PassCode
    {
        FRONT_END,
        BACK_END
    };

    CompilerPass(const RawEvent& event);

    PassCode       PassCode() const;
    const wchar_t* InputSourcePath() const;
    const wchar_t* OutputObjectPath() const;
};
```

## <a name="members"></a>Členové

Spolu se zděděnými členy ze své základní třídy [aktivity](activity.md) obsahuje Třída `CompilerPass` následující členy:

### <a name="constructors"></a>Konstruktory

[CompilerPass](#compiler-pass)

### <a name="enums"></a>Výčty

#### <a name="passcode"></a>Kód

|||
|-|-|
|FRONT_END|Front-end průchod.|
|BACK_END|Back-endové průchod.|

### <a name="functions"></a>Functions

[InputSourcePath](#input-source-path)\
[OutputObjectPath](#output-object-path)\
\ [hesla](#pass-code)

## <a name="compiler-pass"></a>CompilerPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [BACK_END_PASS](../event-table.md#back-end-pass) nebo [FRONT_END_PASS](../event-table.md#front-end-pass) .

## <a name="input-source-path"></a>InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>Návratová hodnota

Absolutní cesta ke vstupnímu zdrojovému souboru zpracovávanému tímto kompilátorem.

## <a name="output-object-path"></a>OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>Návratová hodnota

Absolutní cesta k souboru výstupního objektu vyprodukovaného tímto kompilátorem Pass.

## <a name="pass-code"></a>Kód

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>Návratová hodnota

Kód, který označuje, který průchod kompilátorem je reprezentován tímto objektem CompilerPass.

::: moniker-end
