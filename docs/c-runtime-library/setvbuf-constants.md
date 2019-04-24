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
ms.openlocfilehash: 28c9debf7e51d06cb9a625bb0a52d578ce3142c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268914"
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

## <a name="see-also"></a>Viz také:

[setbuf](../c-runtime-library/reference/setbuf.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
