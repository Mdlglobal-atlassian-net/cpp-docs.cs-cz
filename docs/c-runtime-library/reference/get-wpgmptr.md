---
title: _get_wpgmptr
ms.date: 11/04/2016
api_name:
- _get_wpgmptr
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_wpgmptr
- _get_wpgmptr
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
ms.openlocfilehash: 0cd2dc9c2f82d3dc49a17dc438157233c50b3261
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955575"
---
# <a name="_get_wpgmptr"></a>_get_wpgmptr

Získá aktuální hodnotu globální proměnné **_wpgmptr** .

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_wpgmptr(
   wchar_t **pValue
);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Ukazatel na řetězec, který má být vyplněn aktuální hodnotou proměnné **_wpgmptr** .

## <a name="return-value"></a>Návratová hodnota

Vrátí nulu v případě úspěchu; chybový kód při selhání. Pokud má PValue **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

**_Get_wpgmptr** volejte pouze v případě, že má váš program širší vstupní bod, jako je **wmain ()** nebo **wWinMain ()** . Globální proměnná **_wpgmptr** obsahuje úplnou cestu ke spustitelnému souboru přidruženému k procesu jako řetězec s velkým znakem. Další informace najdete v tématu [_pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_get_pgmptr](get-pgmptr.md)<br/>
