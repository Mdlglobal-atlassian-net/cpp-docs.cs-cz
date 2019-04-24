---
title: Konstanty haldy
ms.date: 11/04/2016
f1_keywords:
- _HEAPBADPTR
- _HEAPEMPTY
- _HEAPBADBEGIN
- _HEAPOK
- _HEAPBADNODE
- _HEAPEND
helpviewer_keywords:
- _HEAPOK constants
- _HEAPEND constants
- HEAPBADBEGIN constants
- _HEAPBADNODE constants
- HEAPBADNODE constants
- HEAPBADPTR constants
- _HEAPEMPTY constants
- HEAPEND constants
- HEAPOK constants
- HEAPEMPTY constants
- _HEAPBADBEGIN constants
- _HEAPBADPTR constants
- heap constants
ms.assetid: 3f751bb9-2dc4-486f-b5f5-9061c96d3754
ms.openlocfilehash: 44c7a280ebffd0073f1dfb3a0a3cbdbd2efee0fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62289595"
---
# <a name="heap-constants"></a>Konstanty haldy

## <a name="syntax"></a>Syntaxe

```
#include <malloc.h>
```

## <a name="remarks"></a>Poznámky

Tyto konstanty poskytnout návratovou hodnotu označující stav haldy.

|Konstanta|Význam|
|--------------|-------------|
|`_HEAPBADBEGIN`|Informace v hlavičce počáteční nebyl nalezen nebo nebyl platný.|
|`_HEAPBADNODE`|Byl nalezen špatný uzel nebo poškození haldy.|
|`_HEAPBADPTR`|**_pentry** pole **_heapinfo –** struktury neobsahuje platný ukazatel do haldy (`_heapwalk` pouze rutina).|
|`_HEAPEMPTY`|Haldy nebyla inicializována.|
|`_HEAPEND`|Bylo úspěšně dosaženo konce haldy (`_heapwalk` pouze rutina).|
|`_HEAPOK`|Halda představuje konzistentní vzhledem k aplikacím (`_heapset` a `_heapchk` pouze rutiny). Zatím; žádné chyby **_Heapinfo –** struktura obsahuje informace o další položce (`_heapwalk` pouze rutina).|

## <a name="see-also"></a>Viz také:

[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
