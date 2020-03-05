---
title: Výčet TRANSLATION_UNIT_PASS_CODE
description: Odkaz C++ na výčet TRANSLATION_UNIT_PASS_CODE Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRANSLATION_UNIT_PASS_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1219eed98fd01e8c91d8750977e2d8ca4498d649
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333578"
---
# <a name="translation_unit_pass_code-enum"></a>Výčet TRANSLATION_UNIT_PASS_CODE

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Výčet `TRANSLATION_UNIT_PASS_CODE`.

## <a name="members"></a>Členové

| Název | Hodnota | Popis |
|--|--|--|
| `TRANSLATION_UNIT_PASS_CODE_FRONT_END` | 0 (0x00000000) | Front-end průchod, který zodpovídá za analýzu zdrojového kódu a převádí ho do zprostředkujícího jazyka. |
| `TRANSLATION_UNIT_PASS_CODE_BACK_END` | 1 (0x00000001) | Back-endové průchod, zodpovídá za optimalizaci zprostředkujícího jazyka a jeho převádění do strojového kódu. |

## <a name="remarks"></a>Poznámky

Používáno funkcemi sady C SDK.

::: moniker-end
