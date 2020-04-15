---
title: výčtFILE_TYPE_CODE
description: C++ Build Insights SDK FILE_TYPE_CODE výčtu odkaz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: dea603a072d7b2f472112a75b2e9ccded78399a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325565"
---
# <a name="file_type_code-enum"></a>výčtFILE_TYPE_CODE

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Výčet `FILE_TYPE_CODE` popisuje typ souboru.

## <a name="members"></a>Členové

| Name (Název) | Hodnota | Popis |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0 (0x00000000) | Typ souboru není uveden v tomto výčtu. |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | Soubor objektu (obj).\* |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2 (0x00000002) | Spustitelný soubor\*( exe) nebo\*DLL ( DLL). |
| `FILE_TYPE_CODE_LIB` | 3 (0x00000003) | Statický soubor knihovny (*.lib). |
| `FILE_TYPE_CODE_IMP_LIB` | 4 (0x00000004) | Knihovna importu (*.lib) |
| `FILE_TYPE_CODE_EXP` | 5 (0x00000005) | Export (*.exp) soubor. |

## <a name="remarks"></a>Poznámky

::: moniker-end
