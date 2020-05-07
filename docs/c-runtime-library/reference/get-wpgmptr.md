---
title: _get_wpgmptr
ms.date: 4/2/2020
api_name:
- _get_wpgmptr
- _o__get_wpgmptr
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: ec21e4967d123c988886fa2e6ab996aad83ef206
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919669"
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

Vrátí nulu v případě úspěchu; chybový kód při selhání. Pokud *pValue* má PValue **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

Volejte **_get_wpgmptr** pouze v případě, že má program širší vstupní bod, například **wmain ()** nebo **wWinMain ()**. Globální proměnná **_wpgmptr** obsahuje úplnou cestu ke spustitelnému souboru, který je přidružený k procesu jako řetězec s velkým znakem. Další informace najdete v tématu [_pgmptr _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_wpgmptr**|\<Stdlib. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_get_pgmptr](get-pgmptr.md)<br/>
