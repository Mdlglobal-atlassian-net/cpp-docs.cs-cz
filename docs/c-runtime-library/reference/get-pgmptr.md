---
title: _get_pgmptr
ms.date: 4/2/2020
api_name:
- _get_pgmptr
- _o__get_pgmptr
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
- get_pgmptr
- _get_pgmptr
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
ms.openlocfilehash: a4a9bddfa861727e174325dc639868e3529162cd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918219"
---
# <a name="_get_pgmptr"></a>_get_pgmptr

Získá aktuální hodnotu globální proměnné **_pgmptr** .

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_pgmptr(
   char **pValue
);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Ukazatel na řetězec, který má být vyplněn aktuální hodnotou proměnné **_pgmptr** .

## <a name="return-value"></a>Návratová hodnota

Vrátí nulu v případě úspěchu; chybový kód při selhání. Pokud *pValue* má PValue **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

Volejte **_get_pgmptr** pouze v případě, že má program úzký vstupní bod, například **Main ()** nebo **WinMain ()**. Globální proměnná **_pgmptr** obsahuje úplnou cestu ke spustitelnému souboru, který je přidružený k procesu. Další informace najdete v tématu [_pgmptr _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_pgmptr**|\<Stdlib. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_get_wpgmptr](get-wpgmptr.md)<br/>
