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
ms.openlocfilehash: 25c25741f54c1383a5bad9038b5b5d761dacdd89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458045"
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
|`_IOFBF`|Úplné ukládání do vyrovnávací paměti: zadané vyrovnávací paměti při volání funkce `setvbuf` se používá a jeho velikost je jako zadané v poli `setvbuf` volání. Pokud je vyrovnávací paměť ukazatele **NULL**, automaticky přidělené vyrovnávací paměti o zadané velikosti se používá.|
|`_IOLBF`|Stejné jako `_IOFBF`.|
|`_IONBF`|Bez vyrovnávací paměti se používá, bez ohledu na to argumentů ve volání `setvbuf`.|

## <a name="see-also"></a>Viz také

[setbuf](../c-runtime-library/reference/setbuf.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)