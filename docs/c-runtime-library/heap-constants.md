---
title: Konstanty haldy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _HEAPBADPTR
- _HEAPEMPTY
- _HEAPBADBEGIN
- _HEAPOK
- _HEAPBADNODE
- _HEAPEND
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 791509a7c67f5fa47128fda97688c43e592724ed
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115174"
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

## <a name="see-also"></a>Viz také

[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)