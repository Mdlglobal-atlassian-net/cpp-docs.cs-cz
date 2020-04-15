---
title: Třída FileInput
description: C++ Build Insights SDK FileInput odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileInput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 642236d3e67465ed38508cb24c8cd698ae880065
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324799"
---
# <a name="fileinput-class"></a>Třída FileInput

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `FileInput` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala [události FILE_INPUT.](../event-table.md#file-input)

## <a name="syntax"></a>Syntaxe

```cpp
class FileInput : public SimpleEvent
{
public:
    enum class Type
    {
        OTHER               = FILE_TYPE_CODE_OTHER,
        OBJ                 = FILE_TYPE_CODE_OBJ,
        EXECUTABLE_IMAGE    = FILE_TYPE_CODE_EXECUTABLE_IMAGE,
        LIB                 = FILE_TYPE_CODE_LIB,
        IMP_LIB             = FILE_TYPE_CODE_IMP_LIB,
        EXP                 = FILE_TYPE_CODE_EXP
    };

    FileInput(const RawEvent& event);

    const wchar_t* Path() const;
    Type           Type() const;
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze základní `FileInput` třídy [SimpleEvent](simple-event.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[FileInput](#file-input)

### <a name="functions"></a>Functions

[Path](#path)
[Typ](#type) cesty

## <a name="fileinput"></a><a name="file-input"></a>FileInput

```cpp
FileInput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost FILE_INPUT.](../event-table.md#file-input)

## <a name="path"></a><a name="path"></a>Cestu

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Návratová hodnota

Absolutní cesta ke vstupnímu souboru.

## <a name="type"></a><a name="type"></a>Typ

```cpp
Type Type() const;
```

### <a name="return-value"></a>Návratová hodnota

Kód popisující typ vstupního souboru.

::: moniker-end
