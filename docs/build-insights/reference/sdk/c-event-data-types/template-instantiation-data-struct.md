---
title: Struktura TEMPLATE_INSTANTIATION_DATA
description: Odkaz C++ na strukturu TEMPLATE_INSTANTIATION_DATA Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa669d715dbe56ce7e889330f46f307f520710f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333620"
---
# <a name="template_instantiation_data-structure"></a>Struktura TEMPLATE_INSTANTIATION_DATA

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

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
| `SpecializationSymbolKey` | Klíč pro typ specializace šablony Tato hodnota je jedinečná v rámci analyzovaného trasování. |
| `PrimaryTemplateSymbolKey` | Klíč pro typ primární šablony, který byl specializovaný. Tato hodnota je jedinečná v rámci analyzovaného trasování. |
| `KindCode` | Typ instance šablony. Další informace najdete v tématu [TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md). |

## <a name="remarks"></a>Poznámky

Klíče ve struktuře `TEMPLATE_INSTANTIATION_DATA` jsou jedinečné v rámci analyzovaného trasování. Nicméně dva různé klíče přicházející z různých front-endové průchody kompilátoru mohou odkazovat na dva identické typy. Při využívání informací `TEMPLATE_INSTANTIATION_DATA` z více front-endového průchodu kompilátoru, použijte události [SYMBOL_NAME](../event-table.md#symbol-name) k určení, zda jsou dva typy stejné. události `SymbolName` jsou generovány na konci front-endu kompilátoru, poté, co byly provedeny všechny instance šablon.

::: moniker-end
