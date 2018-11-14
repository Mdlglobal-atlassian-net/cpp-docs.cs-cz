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
ms.openlocfilehash: 661cf64c71e06c222503388df198d47429566602
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523803"
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