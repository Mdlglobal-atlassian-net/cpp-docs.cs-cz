---
title: Výčet FILE_TYPE_CODE
description: Odkaz C++ na výčet FILE_TYPE_CODE Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e64f9315c62ce40c436032d6c96fdfa725847a7f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333718"
---
# <a name="file_type_code-enum"></a>Výčet FILE_TYPE_CODE

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

`FILE_TYPE_CODE` výčet popisuje typ souboru.

## <a name="members"></a>Členové

| Název | Hodnota | Popis |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0 (0x00000000) | Typ souboru, který není uvedený v tomto výčtu. |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | Soubor objektu (\*. obj). |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2 (0x00000002) | Spustitelný soubor (\*. exe) nebo knihovna DLL (\*. dll). |
| `FILE_TYPE_CODE_LIB` | 3 (0x00000003) | Soubor statické knihovny (*. lib). |
| `FILE_TYPE_CODE_IMP_LIB` | 4 (0x00000004) | Knihovna importu (*. lib) |
| `FILE_TYPE_CODE_EXP` | 5 (0x00000005) | Soubor exportu (*. exp). |

## <a name="remarks"></a>Poznámky

::: moniker-end
