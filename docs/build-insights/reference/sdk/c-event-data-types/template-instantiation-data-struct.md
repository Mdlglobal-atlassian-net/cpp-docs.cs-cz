---
title: TEMPLATE_INSTANTIATION_DATA struktura
description: C++ Build Insights SDK TEMPLATE_INSTANTIATION_DATA odkaz na strukturu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a38d19368e7c0a9912907f1da6e7a2e31ffe8d90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325332"
---
# <a name="template_instantiation_data-structure"></a>TEMPLATE_INSTANTIATION_DATA struktura

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `TEMPLATE_INSTANTIATION_DATA` popisuje vytvoření instance šablony.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct TEMPLATE_INSTANTIATION_DATA_TAG
{
    unsigned long long  SpecializationSymbolKey;
    unsigned long long  PrimaryTemplateSymbolKey;
    int                 KindCode;

} TEMPLATE_INSTANTIATION_DATA;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `SpecializationSymbolKey` | Klíč pro typ specializace šablony. Tato hodnota je jedinečný v rámci trasování analyzovány. |
| `PrimaryTemplateSymbolKey` | Klíč pro typ primární šablony, který byl specializovaný. Tato hodnota je jedinečný v rámci trasování analyzovány. |
| `KindCode` | Typ instance šablony. Další informace naleznete [v tématu TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md). |

## <a name="remarks"></a>Poznámky

Klíče ve `TEMPLATE_INSTANTIATION_DATA` struktuře jsou jedinečné v rámci trasování analyzovány. Dva různé klíče pocházející z různých průchodů front-endkompilátoru však může ukazovat na dva identické typy. Při využívání `TEMPLATE_INSTANTIATION_DATA` informací z více front-endových průchodů kompilátoru použijte [SYMBOL_NAME](../event-table.md#symbol-name) události k určení, zda jsou dva typy stejné. `SymbolName`události jsou vyzařovány na konci front-endu kompilátoru, po všechny instance šablony.

::: moniker-end
