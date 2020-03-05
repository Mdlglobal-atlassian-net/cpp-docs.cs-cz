---
title: Třída vyvolání
description: Odkaz C++ na třídu volání sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0c4698300a3eeaf77210ad74f84b0c0cd219b457
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333228"
---
# <a name="invocation-class"></a>Třída vyvolání

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Invocation` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke shodě s [kompilátorem](../event-table.md#compiler) nebo událostí [linkeru](../event-table.md#linker) .

## <a name="syntax"></a>Syntaxe

```cpp
class Invocation : public Activity
{
    const INVOCATION_DATA* data_;

public:
    enum class Type
    {
        CL      = MSVC_TOOL_CODE_CL,
        LINK    = MSVC_TOOL_CODE_LINK
    };

    Invocation(const RawEvent& event);

    Type             Type() const;
    const char*      ToolVersionString() const;
    const wchar_t*   WorkingDirectory() const;
    const wchar_t*   ToolPath() const;

    const INVOCATION_VERSION_DATA& ToolVersion() const;
};
```

## <a name="members"></a>Členové

Spolu se zděděnými členy ze své základní třídy [aktivity](activity.md) obsahuje Třída `Invocation` následující členy:

### <a name="constructors"></a>Konstruktory

[Vyvolání](#invocation)

### <a name="functions"></a>Functions

[ToolPath](#tool-path)
[ToolVersion](#tool-version)
[ToolVersionString](#tool-version-string)
[typ](#type)
[WorkingDirectory](#working-directory)

## <a name="invocation"></a>Vyvolání

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [kompilátoru](../event-table.md#compiler) nebo [linkeru](../event-table.md#linker) .

## <a name="tool-path"></a>ToolPath

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>Návratová hodnota

Absolutní cesta k vyvolanému nástroji.

## <a name="tool-version"></a>ToolVersion

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>Návratová hodnota

Verze nástroje, která byla vyvolána, jako odkaz [INVOCATION_VERSION_DATA](../c-event-data-types/invocation-version-data-struct.md) .

## <a name="tool-version-string"></a>ToolVersionString

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>Návratová hodnota

Verze nástroje, která byla vyvolána, jako řetězec ANSI.

## <a name="type"></a>Textový

```cpp
Type Type() const;
```

### <a name="return-value"></a>Návratová hodnota

Kód označující, který nástroj byl vyvolán.

## <a name="working-directory"></a>WorkingDirectory

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>Návratová hodnota

Absolutní cesta k adresáři, ve kterém byl nástroj vyvolán.

::: moniker-end
