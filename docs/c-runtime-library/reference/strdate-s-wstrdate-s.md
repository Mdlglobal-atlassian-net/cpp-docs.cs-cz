---
title: _strdate_s, _wstrdate_s
description: _strdate_s a _wstrdate_s jsou zabezpečené crt verze _strdate a _wstrdate funkce, které umístit aktuální datum do vyrovnávací paměti.
ms.date: 4/2/2020
api_name:
- _strdate_s
- _wstrdate_s
- _o__strdate_s
- _o__wstrdate_s
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _strdate_s
- wstrdate_s
- _wstrdate_s
- strdate_s
- _tstrdate_s
helpviewer_keywords:
- dates, copying
- tstrdate_s function
- wstrdate_s function
- _tstrdate_s function
- strdate_s function
- copying dates
- _strdate_s function
- _wstrdate_s function
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
ms.openlocfilehash: b4d977ba3546eae17218c63b1786fd26c784d340
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359825"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s, _wstrdate_s

Zkopírujte aktuální systémové datum do vyrovnávací paměti. Tyto funkce jsou verze [_strdate, _wstrdate](strdate-wstrdate.md) s vylepšeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _strdate_s(
   char *buffer,
   size_t size
);
errno_t _wstrdate_s(
   wchar_t *buffer,
   size_t size
);
template <size_t size>
errno_t _strdate_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrdate_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*\
Ukazatel na vyrovnávací paměť pro umístění formátovaného řetězce kalendářních dat.

*Velikost*\
Velikost vyrovnávací paměti v jednotkách znaků.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud došlo k chybě. Kódy chyb jsou definovány v ERRNO. H; přesné chyby generované touto funkcí naleznete v tabulce níže. Další informace o kódech chyb naleznete [v tématu errno](../../c-runtime-library/errno-constants.md).

## <a name="error-conditions"></a>Chybové stavy

|*Vyrovnávací paměti*|*Velikost*|Vrátit|Obsah *vyrovnávací paměti*|
|--------------|------------------------|------------|--------------------------|
|**Null**|(libovolná)|**EINVAL**|Nezměněno|
|Ne **null** (ukazuje na platnou vyrovnávací paměť)|0|**EINVAL**|Nezměněno|
|Ne **null** (ukazuje na platnou vyrovnávací paměť)|0 < *velikost* < 9|**EINVAL**|Prázdný řetězec|
|Ne **null** (ukazuje na platnou vyrovnávací paměť)|*velikost* >= 9|0|Aktuální datum formátované podle poznámek|

## <a name="security-issues"></a>Problémy se zabezpečením

Předání neplatné hodnoty bez hodnoty NULL pro *vyrovnávací paměť* má za následek narušení přístupu, pokud je parametr *velikosti* větší než devět.

Předání hodnoty pro *velikost* větší než skutečná velikost *vyrovnávací paměti* má za následek přetečení vyrovnávací paměti.

## <a name="remarks"></a>Poznámky

Tyto funkce poskytují bezpečnější verze **_strdate** a **_wstrdate**. Funkce **_strdate_s** zkopíruje aktuální systémové datum do vyrovnávací paměti, na kterou je ve *vyrovnávací paměti.* Je formátován `mm/dd/yy`, `mm` kde je dvoumístný měsíc, `dd` je dvoumístný den a `yy` je poslední dvě číslice roku. Například řetězec `12/05/99` představuje prosinec 5, 1999. Vyrovnávací paměť musí mít alespoň devět znaků.

**_wstrdate_s** je širokoznaková verze **_strdate_s**; argument a vrácená hodnota **_wstrdate_s** jsou řetězce širokých znaků. Tyto funkce se chovají stejně jinak.

Pokud je *vyrovnávací paměť* ukazatelem **NULL** nebo *velikost* je menší než devět znaků, je vyvolána neplatná obslužná rutina parametru. Je popsána v [parametru Ověření](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí -1. Nastaví **errno** na **EINVAL,** pokud je vyrovnávací paměť **NULL** nebo pokud je *velikost* menší nebo rovna 0. Nebo nastaví **errno** na **ERANGE,** pokud je *velikost* menší než 9.

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony. Přetížení lze odvodit délku vyrovnávací paměti automaticky, což eliminuje potřebu zadat argument *velikosti.* A mohou automaticky nahradit nezabezpečené funkce svými novějšími a bezpečnějšími protějšky. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze knihovny těchto funkcí nejprve vyplní vyrovnávací paměť 0xFE. Chcete-li toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mapování rutiny obecného textu:

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<time.h> \<nebo wchar.h>|
|**_strdate_s**|\<time.h>|

## <a name="example"></a>Příklad

Viz příklad [pro čas](time-time32-time64.md).

## <a name="see-also"></a>Viz také

[Řízení času](../../c-runtime-library/time-management.md)\
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)\
[ctime_s, _ctime32_s, _ctime64_s _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)\
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)\
[čas, _time32, _time64](time-time32-time64.md)\
[_tzset](tzset.md)
