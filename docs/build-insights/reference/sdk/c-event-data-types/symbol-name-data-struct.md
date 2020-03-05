---
title: Struktura SYMBOL_NAME_DATA
description: Odkaz C++ na strukturu SYMBOL_NAME_DATA Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 618e84f198c20aa089dc7e06e1e6c09b96b6d273
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333634"
---
# <a name="symbol_name_data-structure"></a>Struktura SYMBOL_NAME_DATA

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

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
| `Key` | Klíč symbolu. Tato hodnota je jedinečná v rámci analyzovaného trasování. |
| `Name` | Název symbolu. |

## <a name="remarks"></a>Poznámky

Symboly přicházející ze dvou různých průchodů front-end kompilátoru mohou mít stejný název, ale jiný klíč. V takovém případě použijte názvy symbolů k určení, zda jsou dva typy stejné.

::: moniker-end
