---
title: _get_doserrno
ms.date: 4/2/2020
api_name:
- _get_doserrno
- _o__get_doserrno
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_doserrno
- get_doserrno
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: 2d5d4e224b39e9fa597e12975d27fa5720fbfbc7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345259"
---
# <a name="_get_doserrno"></a>_get_doserrno

Získá chybovou hodnotu vrácenou operačním systémem před tím, než je přeložen do hodnoty **errno.**

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>Parametry

*pHodnota*<br/>
Ukazatel na celé číslo, které má být vyplněno aktuální hodnotou **_doserrno** globální makro.

## <a name="return-value"></a>Návratová hodnota

Pokud **_get_doserrno** úspěšné, vrátí nulu; Pokud se nezdaří, vrátí kód chyby. Pokud je *hodnota pValue* **null**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **Funkce EINVAL**.

## <a name="remarks"></a>Poznámky

Globální **makro _doserrno** je nastavena na nulu během inicializace CRT před zahájením provádění procesu. Je nastavena na hodnotu chyby operačního systému vrácené volání mandatáře na úrovni systému, které vrací chybu operačního systému a během spuštění se nikdy neresetuje na nulu. Při psaní kódu pro kontrolu chybové hodnoty vrácené funkcí vždy zrušte **_doserrno** pomocí [_set_doserrno](set-doserrno.md) před voláním funkce. Vzhledem k tomu, že jiné volání funkce může přepsat **_doserrno**, zkontrolujte hodnotu pomocí **_get_doserrno** ihned po volání funkce.

Doporučujeme [_get_errno](get-errno.md) místo **_get_doserrno** pro přenosné chybové kódy.

Možné hodnoty **_doserrno** jsou \<definovány v> errno.h.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|

**_get_doserrno** je rozšíření společnosti Microsoft. Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
