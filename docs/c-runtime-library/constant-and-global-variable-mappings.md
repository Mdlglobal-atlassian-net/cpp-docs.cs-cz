---
title: Mapování konstant a globálních proměnných
ms.date: 11/04/2016
f1_keywords:
- _tenviron
- _TEOF
- _tfinddata_t
helpviewer_keywords:
- tfinddatat function
- tenviron function
- TEOF type
- _TEOF type
- generic-text mappings
- _tenviron function
- _tfinddata_t function
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
ms.openlocfilehash: 1bd96c7a305f588a24b0c6d31b2a0132d6546574
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750192"
---
# <a name="constant-and-global-variable-mappings"></a>Mapování konstant a globálních proměnných

Tyto konstantu obecného textu, globální proměnné a mapování typu standard jsou definovány v TCHAR. H a závisí na tom, zda konstanty `_UNICODE` nebo `_MBCS` je definována v programu.

### <a name="generic-text-constant-and-global-variable-mappings"></a>Mapování obecného textu konstant a globálních proměnných

|Obecné textové – název objektu|SBCS (_UNICODE, _MBCS nejsou definovány)|_MBCS definováno|_UNICODE definováno|
|----------------------------------|--------------------------------------------|--------------------|-----------------------|
|`_TEOF`|`EOF`|`EOF`|`WEOF`|
|`_tenviron`|`_environ`|`_environ`|`_wenviron`|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="see-also"></a>Viz také:

[Mapování obecného textu](../c-runtime-library/generic-text-mappings.md)<br/>
[Mapování datového typu](../c-runtime-library/data-type-mappings.md)<br/>
[Mapování rutin](../c-runtime-library/routine-mappings.md)<br/>
[Ukázka programu obecného textu](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[Použití mapování obecného textu](../c-runtime-library/using-generic-text-mappings.md)
