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
ms.openlocfilehash: 89609de3fc5584a960480bff83566f5e38c8be1f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62342481"
---
# <a name="path-field-limits"></a>Omezení pole cesty

## <a name="syntax"></a>Syntaxe

```cpp
#include <stdlib.h>
```

## <a name="remarks"></a>Poznámky

Tyto konstanty určit maximální délku pro cestu a pro jednotlivá pole v této cestě.

|Konstanta|Význam|
|--------------|-------------|
|`_MAX_DIR`|Maximální délka součásti adresáře|
|`_MAX_DRIVE`|Maximální délka součásti jednotky|
|`_MAX_EXT`|Maximální délka součásti rozšíření|
|`_MAX_FNAME`|Maximální délka názvu souboru součásti|
|`_MAX_PATH`|Maximální délka úplné cesty|

> [!NOTE]
> Modul Runtime jazyka C podporuje délky cesty až 32768 znaků dlouhé, ale je operační systém, konkrétně systému souborů, pro podporu těchto cest delší dobu. Součet z polí by neměly být delší než `_MAX_PATH` úplného zpětnou kompatibilitu s FAT32 systémů souborů. Systém souborů Windows NTFS podporuje cesty až 32768 znaků délku, ale jenom při použití rozhraní API pro kódování Unicode. Při použití dlouhé názvy cest, předponová cesta se znaky \\ \\? \ a používat Unicode verze funkce C Runtime.

## <a name="see-also"></a>Viz také:

[Globální konstanty](../c-runtime-library/global-constants.md)