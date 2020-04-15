---
title: SYMBOL_NAME_DATA struktura
description: C++ Build Insights SDK SYMBOL_NAME_DATA odkaz na strukturu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1217572f20a772fde629533d6ab170c14dc5b5e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325342"
---
# <a name="symbol_name_data-structure"></a>SYMBOL_NAME_DATA struktura

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `SYMBOL_NAME_DATA` popisuje symbol front-endu kompilátoru.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `Key` | Klíč symbolu. Tato hodnota je jedinečný v rámci trasování analyzovány. |
| `Name` | Jméno symbolu. |

## <a name="remarks"></a>Poznámky

Symboly pocházející ze dvou různých průchodů front-endu kompilátoru mohou mít stejný název, ale jiný klíč. V takovém případě použijte názvy symbolů k určení, zda jsou dva typy stejné.

::: moniker-end
