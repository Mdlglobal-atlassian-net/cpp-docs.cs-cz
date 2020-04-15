---
title: Třída FileOutput
description: C++ Build Insights SDK FileOutput odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 37823da8a4aaac0ce4094583b8aee8ac1eb04aaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324806"
---
# <a name="fileoutput-class"></a>Třída FileOutput

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `FileOutput` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Slouží k tomu, aby odpovídala události [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output), [LIB_OUTPUT](../event-table.md#lib-output)nebo [OBJ_OUTPUT.](../event-table.md#obj-output)

## <a name="syntax"></a>Syntaxe

```cpp
class FileOutput : public SimpleEvent
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

    FileOutput(const RawEvent& event);

    const wchar_t* Path() const;
    Type           Type() const;
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze základní `FileOutput` třídy [SimpleEvent](simple-event.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[Výstup souboru](#file-output)

### <a name="functions"></a>Functions

[Path](#path)
[Typ](#type) cesty

## <a name="fileoutput"></a><a name="file-output"></a>Výstup souboru

```cpp
FileOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
Událost [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output), [LIB_OUTPUT](../event-table.md#lib-output)nebo [OBJ_OUTPUT.](../event-table.md#obj-output)

## <a name="path"></a><a name="path"></a>Cestu

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Návratová hodnota

Absolutní cesta k výstupnímu souboru.

## <a name="type"></a><a name="type"></a>Typ

```cpp
Type Type() const;
```

### <a name="return-value"></a>Návratová hodnota

Kód popisující typ výstupního souboru.

::: moniker-end
