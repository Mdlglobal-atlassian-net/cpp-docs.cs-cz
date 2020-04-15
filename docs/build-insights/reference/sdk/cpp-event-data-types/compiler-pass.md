---
title: Třída CompilerPass
description: C++ Build Insights SDK CompilerPass odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 11af981b647d5183f88dad024d90c0ef4f8a28bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325047"
---
# <a name="compilerpass-class"></a>Třída CompilerPass

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `CompilerPass` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala [události BACK_END_PASS](../event-table.md#back-end-pass) nebo [FRONT_END_PASS.](../event-table.md#front-end-pass)

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

Spolu s zděděnými členy ze `CompilerPass` základní třídy [Aktivita](activity.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[KompilátorPass](#compiler-pass)

### <a name="enums"></a>Výčty

#### <a name="passcode"></a>Heslo

|||
|-|-|
|FRONT_END|Front-end přihrávka.|
|BACK_END|Back-end přihrávka.|

### <a name="functions"></a>Functions

[InputSourcePath](#input-source-path)\
[OutputObjectPath](#output-object-path)\
[Heslo](#pass-code)\

## <a name="compilerpass"></a><a name="compiler-pass"></a>KompilátorPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
Událost [BACK_END_PASS](../event-table.md#back-end-pass) nebo [FRONT_END_PASS.](../event-table.md#front-end-pass)

## <a name="inputsourcepath"></a><a name="input-source-path"></a>InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>Návratová hodnota

Absolutní cesta k vstupnímu zdrojovému souboru zpracovanému tímto průchodem kompilátoru.

## <a name="outputobjectpath"></a><a name="output-object-path"></a>OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>Návratová hodnota

Absolutní cesta k výstupnímu souboru objektu vytvořeného tímto průchodem kompilátoru.

## <a name="passcode"></a><a name="pass-code"></a>Heslo

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>Návratová hodnota

Kód označující, který kompilátor průchod je reprezentován tento CompilerPass objektu.

::: moniker-end
