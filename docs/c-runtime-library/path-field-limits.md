---
title: Omezení pole cesty
ms.date: 11/04/2016
f1_keywords:
- _MAX_EXT
- _MAX_DIR
- _MAX_PATH
- _MAX_FNAME
- _MAX_DRIVE
helpviewer_keywords:
- path field constants
- MAX_FNAME constant
- _MAX_DIR constant
- _MAX_DRIVE constant
- paths, maximum limit
- _MAX_PATH constant
- MAX_DRIVE constant
- _MAX_FNAME constant
- _MAX_EXT constant
- MAX_DIR constant
- MAX_EXT constant
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
ms.openlocfilehash: 8db9961bd2d5b5b3ea9d3addad3c26737b4f5199
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171395"
---
# <a name="path-field-limits"></a>Omezení pole cesty

## <a name="syntax"></a>Syntaxe

```cpp
#include <stdlib.h>
```

## <a name="remarks"></a>Poznámky

Tyto konstanty definují maximální délku cesty a pro jednotlivá pole v rámci cesty.

|Trvalé|Význam|
|--------------|-------------|
|`_MAX_DIR`|Maximální délka součásti adresáře|
|`_MAX_DRIVE`|Maximální délka součásti jednotky|
|`_MAX_EXT`|Maximální délka součásti rozšíření|
|`_MAX_FNAME`|Maximální délka součásti filename|
|`_MAX_PATH`|Maximální délka úplné cesty|

> [!NOTE]
> Modul runtime jazyka C podporuje délku cesty až 32768 znaků, ale je až do operačního systému, konkrétně do systému souborů, aby podporoval tyto delší cesty. Součet polí by neměl překročit `_MAX_PATH` pro úplnou zpětnou kompatibilitu se systémy souborů FAT32. Systém souborů NTFS systému Windows podporuje cesty dlouhé až 32768 znaků, ale pouze při použití rozhraní Unicode API. Při použití dlouhých názvů cest použijte předponu cesty se znaky \\\\? \ a používejte verze Unicode běhových funkcí jazyka C.

## <a name="see-also"></a>Viz také

[Globální konstanty](../c-runtime-library/global-constants.md)
