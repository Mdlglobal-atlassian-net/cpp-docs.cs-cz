---
title: setvbuf – konstanty
ms.date: 11/04/2016
f1_keywords:
- _IOFBF
- _IONBF
- _IOLBF
helpviewer_keywords:
- _IOFBF constant
- IOFBF constant
- IONBF constant
- _IOLBF constant
- IOLBF constant
- _IONBF constant
ms.assetid: a6ec4dd5-1f24-498c-871a-e874cd28d33c
ms.openlocfilehash: 8936789f4e3c9349e9d79616c8506c044dc79f70
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220397"
---
# <a name="setvbuf-constants"></a>setvbuf – konstanty

## <a name="syntax"></a>Syntaxe

```
#include <stdio.h>
```

## <a name="remarks"></a>Poznámky

Tyto konstanty představují typ vyrovnávací paměti pro `setvbuf`.

Možné hodnoty jsou uvedeny následující konstanty manifestu:

|Konstanta|Význam|
|--------------|-------------|
|`_IOFBF`|Úplné ukládání do vyrovnávací paměti: Vyrovnávací paměť určená při volání funkce `setvbuf` se používá a jeho velikost je jako zadané v poli `setvbuf` volání. Pokud je vyrovnávací paměť ukazatele **NULL**, automaticky přidělené vyrovnávací paměti o zadané velikosti se používá.|
|`_IOLBF`|Stejné jako `_IOFBF`.|
|`_IONBF`|Bez vyrovnávací paměti se používá, bez ohledu na to argumentů ve volání `setvbuf`.|

## <a name="see-also"></a>Viz také

[setbuf](../c-runtime-library/reference/setbuf.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
