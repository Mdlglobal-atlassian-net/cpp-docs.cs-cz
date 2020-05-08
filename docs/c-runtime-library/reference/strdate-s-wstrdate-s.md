---
title: _strdate_s, _wstrdate_s
description: _strdate_s a _wstrdate_s jsou zabezpečené verze CRT _strdate a _wstrdate funkce, které vloží aktuální datum do vyrovnávací paměti.
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 7fe8d682ab515d5a11e90f0c26e956725644806e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916919"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s, _wstrdate_s

Zkopírujte aktuální systémové datum do vyrovnávací paměti. Tyto funkce jsou verze [_strdate, _wstrdate](strdate-wstrdate.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*vyrovnávací paměti*\
Ukazatel na vyrovnávací paměť pro vložení formátovaného řetězce data.

*hodnota*\
Velikost vyrovnávací paměti v jednotkách znaků.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Návratová hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v ERRNO. Y v tabulce níže najdete přesné chyby generované touto funkcí. Další informace o kódech chyb naleznete v tématu [errno](../../c-runtime-library/errno-constants.md).

## <a name="error-conditions"></a>Chybové stavy

|*vyrovnávací paměti*|*hodnota*|Vrátit|Obsah *vyrovnávací paměti*|
|--------------|------------------------|------------|--------------------------|
|**PLATNOST**|jakýmikoli|**EINVAL**|Neupraveno|
|NOT **null** (ukazující na platnou vyrovnávací paměť)|0|**EINVAL**|Neupraveno|
|NOT **null** (ukazující na platnou vyrovnávací paměť)|0 < *velikosti* < 9|**EINVAL**|Prázdný řetězec|
|NOT **null** (ukazující na platnou vyrovnávací paměť)|*velikost* >= 9|0|Aktuální datum ve formátu, jak je uvedeno v komentářích|

## <a name="security-issues"></a>Problémy se zabezpečením

Předání neplatné, nenulové hodnoty pro *vyrovnávací paměť* má za následek porušení přístupu, pokud je parametr *Size* větší než devět.

Předání hodnoty *velikosti* větší než skutečná velikost *vyrovnávací paměti* způsobí přetečení vyrovnávací paměti.

## <a name="remarks"></a>Poznámky

Tyto funkce poskytují bezpečnější verze **_strdate** a **_wstrdate**. Funkce **_strdate_s** zkopíruje aktuální systémové datum do vyrovnávací paměti, na kterou ukazuje *vyrovnávací paměť*. Je ve formátu `mm/dd/yy`, kde `mm` je dvouciferné měsíc, `dd` je dvouciferné číslo dne a `yy` jedná se o poslední dvě číslice roku. Například řetězec `12/05/99` představuje 5. prosince 1999. Vyrovnávací paměť musí mít aspoň devět znaků.

**_wstrdate_s** je verze **_strdate_s**s velkým znakem; argument a návratová hodnota **_wstrdate_s** jsou řetězce s velkým počtem znaků. Tyto funkce se chovají identicky jinak.

Pokud je *vyrovnávací paměť* ukazatel s **hodnotou null** nebo je *Velikost* menší než devět znaků, je vyvolána obslužná rutina neplatného parametru. Je popsána v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce hodnotu-1. Nastaví **errno** na **EINVAL** , pokud je vyrovnávací paměť **null** nebo pokud je *Velikost* menší nebo rovna 0. Nebo nastaví **errno** na **ERANGE** , pokud je *Velikost* menší než 9.

V jazyce C++ je použití těchto funkcí zjednodušeno pomocí přetížení šablon. Přetížení můžou odvodit délku vyrovnávací paměti automaticky, což eliminuje nutnost zadat argument *Size* . A můžou automaticky nahradit nezabezpečené funkce jejich novějšími, bezpečnějšími protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Verze knihovny ladění těchto funkcí nejprve naplní vyrovnávací paměť pomocí 0xFE. K zakázání tohoto chování použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mapování rutiny obecného textu:

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strdate**|\<Time. h>|
|**_wstrdate**|\<Time. h> nebo \<WCHAR. h>|
|**_strdate_s**|\<Time. h>|

## <a name="example"></a>Příklad

Podívejte se na příklad pro [čas](time-time32-time64.md).

## <a name="see-also"></a>Viz také

[Správa času](../../c-runtime-library/time-management.md)\
[asctime_s _wasctime_s](asctime-s-wasctime-s.md)\
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)\
[gmtime_s, _gmtime32_s _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s, _localtime32_s _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32 _mktime64](mktime-mktime32-mktime64.md)\
[čas, _time32 _time64](time-time32-time64.md)\
[_tzset](tzset.md)
