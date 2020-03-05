---
title: Třída Output
description: Odkaz C++ na třídu výstupu sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1c4053d0378ddb9d5dd061bbc9889c454dc9b52c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333340"
---
# <a name="fileoutput-class"></a>Třída Output

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `FileOutput` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ji ke spárování [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output)události [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output), [LIB_OUTPUT](../event-table.md#lib-output)nebo [OBJ_OUTPUT](../event-table.md#obj-output) .

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

Společně s děděnými členy ze své základní třídy [SimpleEvent](simple-event.md) obsahuje Třída `FileOutput` následující členy:

### <a name="constructors"></a>Konstruktory

[Výstup](#file-output)

### <a name="functions"></a>Functions

[Typ](#type)
[cesty](#path)

## <a name="file-output"></a>Výstup

```cpp
FileOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output), [LIB_OUTPUT](../event-table.md#lib-output)nebo [OBJ_OUTPUT](../event-table.md#obj-output) .

## <a name="path"></a>Dílčí

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Návratová hodnota

Absolutní cesta k výstupnímu souboru.

## <a name="type"></a>Textový

```cpp
Type Type() const;
```

### <a name="return-value"></a>Návratová hodnota

Kód popisující typ výstupního souboru.

::: moniker-end
