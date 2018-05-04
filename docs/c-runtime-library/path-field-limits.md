---
title: Omezení pole cesty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _MAX_EXT
- _MAX_DIR
- _MAX_PATH
- _MAX_FNAME
- _MAX_DRIVE
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0672245a87cdbcf2a4a6dba6d36c675f3faafbc5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="path-field-limits"></a>Omezení pole cesty

## <a name="syntax"></a>Syntaxe

```cpp
#include <stdlib.h>
```

## <a name="remarks"></a>Poznámky

Tyto konstanty určit maximální délku cesty a jednotlivých polí v této cestě.

|Konstanta|Význam|
|--------------|-------------|
|`_MAX_DIR`|Maximální délka directory součásti|
|`_MAX_DRIVE`|Maximální délka jednotky součásti|
|`_MAX_EXT`|Maximální délka součásti rozšíření|
|`_MAX_FNAME`|Maximální délka součástí názvu souboru|
|`_MAX_PATH`|Maximální délka úplné cesty|

> [!NOTE]
> C Runtime podporuje délka délky cesty až 32768 znaků, ale je až operačního systému, speciálně systému souborů, pro podporu těchto delší cesty. Součet pole nesmí být delší než `_MAX_PATH` pro úplné zpětné kompatibility s FAT32 systémy souborů. Systému souborů Windows NTFS podporuje cesty až 32768 znaků délka, ale jenom v případě, že pomocí rozhraní API kódování Unicode. Při použití dlouhé názvy cest, předpony cestu s znaky \\ \\? \ a použít Unicode verze funkce C Runtime.

## <a name="see-also"></a>Viz také

[Globální konstanty](../c-runtime-library/global-constants.md)