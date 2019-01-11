---
title: fseek, _lseek – konstanty
ms.date: 11/04/2016
f1_keywords:
- SEEK_END
- SEEK_SET
- SEEK_CUR
helpviewer_keywords:
- SEEK_SET constant
- SEEK_END constant
- SEEK_CUR constant
ms.assetid: 9deeb13e-5aa3-4c33-80d8-721c80a4de9d
ms.openlocfilehash: a97495aaa5ab0a79ed71a48a12162bd14fc60131
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220449"
---
# <a name="fseek-lseek-constants"></a>fseek, _lseek – konstanty

## <a name="syntax"></a>Syntaxe

```
#include <stdio.h>
```

## <a name="remarks"></a>Poznámky

*Původu* argument určuje počáteční pozici a může být jedna z následujících konstant manifestu:

|Konstanta|Význam|
|--------------|-------------|
|`SEEK_END`|Konec souboru|
|`SEEK_CUR`|Aktuální pozici ukazatele na soubor|
|`SEEK_SET`|Začátek souboru|

## <a name="see-also"></a>Viz také

[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
