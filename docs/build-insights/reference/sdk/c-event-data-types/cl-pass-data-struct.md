---
title: CL_PASS_DATA struktura
description: C++ Sestavení Insights SDK CL_PASS_DATA struktura odkaz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b0a41e59068ade285f1ffa1a9ce13734ef5f1f32
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325702"
---
# <a name="cl_pass_data-structure"></a>CL_PASS_DATA struktura

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `CL_PASS_DATA` popisuje kompilace průchod.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct CL_PASS_DATA_TAG
{
    int                         TranslationUnitPassCode;
    const wchar_t*              InputSourcePath;
    const wchar_t*              OutputObjectPath;

} CL_PASS_DATA;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `TranslationUnitPassCode` | Kód identifikující kompilaci průchod uprovádění. Další informace naleznete [v tématu TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md). |
| `InputSourcePath` | Zdrojový soubor C nebo C++, ve kterém je tento průchod kompilace prováděn. |
| `OutputObjectPath` | Soubor objektu vytvářený kompilátorem. |

::: moniker-end
