---
title: Třída vyvolání
description: C++ Build Insights SDK vyvolání třídy odkaz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fcb087d46ea445251b0108f811545a44c26f421e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324645"
---
# <a name="invocation-class"></a>Třída vyvolání

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Invocation` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala události [KOMPILÁTORU](../event-table.md#compiler) nebo [LINKER.](../event-table.md#linker)

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

Spolu s zděděnými členy ze `Invocation` základní třídy [Aktivita](activity.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[Vyvolání](#invocation)

### <a name="functions"></a>Functions

[Typ](#tool-path)

[pracovního adresáře](#working-directory) typu WorkingDirectory typu ToolPath[ToolVersion](#tool-version)
[Toolversion](#tool-version-string)
[Type](#type)

## <a name="invocation"></a><a name="invocation"></a>Vyvolání

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Kompilace](../event-table.md#compiler) nebo [LINKER](../event-table.md#linker) událost.

## <a name="toolpath"></a><a name="tool-path"></a>Cesta nástroje

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>Návratová hodnota

Absolutní cesta k nástroji, který byl vyvolán.

## <a name="toolversion"></a><a name="tool-version"></a>Verze nástroje

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>Návratová hodnota

Verze nástroje, který byl vyvolán jako [odkaz INVOCATION_VERSION_DATA.](../c-event-data-types/invocation-version-data-struct.md)

## <a name="toolversionstring"></a><a name="tool-version-string"></a>ToolVersionString

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>Návratová hodnota

Verze nástroje, který byl vyvolán jako řetězec ANSI.

## <a name="type"></a><a name="type"></a>Typ

```cpp
Type Type() const;
```

### <a name="return-value"></a>Návratová hodnota

Kód označující nástroj, který byl vyvolán.

## <a name="workingdirectory"></a><a name="working-directory"></a>WorkingDirectory

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>Návratová hodnota

Absolutní cesta k adresáři, ve kterém byl nástroj vyvolán.

::: moniker-end
