---
title: Třída Input
description: Odkaz C++ na třídu vstupu sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileInput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bea2cf72ca2a83a9cd630f8a9ccefb87dd4b7ff1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333347"
---
# <a name="fileinput-class"></a>Třída Input

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `FileInput` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [FILE_INPUT](../event-table.md#file-input) události.

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

Společně s děděnými členy ze své základní třídy [SimpleEvent](simple-event.md) obsahuje Třída `FileInput` následující členy:

### <a name="constructors"></a>Konstruktory

[Vstup vstupu](#file-input)

### <a name="functions"></a>Functions

[Typ](#type)
[cesty](#path)

## <a name="file-input"></a>Vstup vstupu

```cpp
FileInput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [FILE_INPUT](../event-table.md#file-input) .

## <a name="path"></a>Dílčí

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Návratová hodnota

Absolutní cesta ke vstupnímu souboru.

## <a name="type"></a>Textový

```cpp
Type Type() const;
```

### <a name="return-value"></a>Návratová hodnota

Kód popisující typ vstupního souboru.

::: moniker-end
