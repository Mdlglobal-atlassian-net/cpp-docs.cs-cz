---
title: _strdate_s, _wstrdate_s
ms.date: 11/04/2016
api_name:
- _strdate_s
- _wstrdate_s
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
ms.openlocfilehash: fadd30ec81cff59d675212e59c8513656c7b2f35
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940755"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s, _wstrdate_s

Zkopírujte aktuální systémové datum do vyrovnávací paměti. Jedná se o verze [_strdate, _wstrdate](strdate-wstrdate.md) s vylepšeními zabezpečení, jak [je popsáno v části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _strdate_s(
   char *buffer,
   size_t numberOfElements
);
errno_t _wstrdate_s(
   wchar_t *buffer,
   size_t numberOfElements
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

*vyrovnávací paměti*<br/>
Ukazatel na vyrovnávací paměť, která bude vyplněna řetězcem formátovaného data.

*numberOfElements*<br/>
Velikost vyrovnávací paměti.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Návratová hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v ERRNO. Y v tabulce níže najdete přesné chyby generované touto funkcí. Další informace o kódech chyb naleznete v tématu [errno](../../c-runtime-library/errno-constants.md).

## <a name="error-conditions"></a>Chybové stavy

|*vyrovnávací paměti*|*numberOfElements*|vrátit|Obsah *vyrovnávací paměti*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|jakýmikoli|**EINVAL**|Neupraveno|
|NOT **null** (ukazující na platnou vyrovnávací paměť)|0|**EINVAL**|Neupraveno|
|NOT **null** (ukazující na platnou vyrovnávací paměť)|0 < *numberOfElements* < 9|**EINVAL**|Prázdný řetězec|
|NOT **null** (ukazující na platnou vyrovnávací paměť)|*numberOfElements* > = 9|0|Aktuální datum ve formátu, jak je uvedeno v komentářích|

## <a name="security-issues"></a>Problémy se zabezpečením

Předání neplatné **nenulové** hodnoty pro vyrovnávací paměť způsobí porušení přístupu, pokud je parametr *numberOfElements* větší než 9.

Předání hodnot velikosti, která je větší než skutečná velikost *vyrovnávací paměti* , způsobí přetečení vyrovnávací paměti.

## <a name="remarks"></a>Poznámky

Tyto funkce poskytují bezpečnější verze **_strdate** a **_wstrdate**. Funkce **_strdate_s** zkopíruje aktuální systémové datum do vyrovnávací paměti, na kterou ukazuje *vyrovnávací paměť*, formátovanou **mm**/**DD**/**RR**, kde **mm** jsou dvě číslice představující měsíc, **DD** představují dvě číslice představující den a **YY** jsou poslední dvě číslice roku. Například řetězec **12/05/99** představuje 5. prosince 1999. Vyrovnávací paměť musí být aspoň 9 znaků dlouhá.

**_wstrdate_s** je **_strdate_s**verze s velkým znakem; argument a návratová hodnota **_wstrdate_s** jsou řetězce s velkým počtem znaků. Tyto funkce se chovají identicky jinak.

Pokud je *vyrovnávací paměť* ukazatel s **hodnotou null** , nebo pokud je *numberOfElements* méně než 9 znaků, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce-1 a nastaví **errno** na **EINVAL** , pokud vyrovnávací paměť má **hodnotu null** nebo pokud je *numberOfElements* menší nebo rovna 0, nebo nastavte **errno** na **ERANGE** , pokud *numberOfElements* je menší než 9.

V C++systému je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují nutnost zadat argument velikosti) a můžou automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mapping"></a>Mapování rutiny obecného textu:

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<Time. h > nebo \<WCHAR. h >|
|**_strdate_s**|\<time.h>|

## <a name="example"></a>Příklad

Podívejte se na příklad pro [čas](time-time32-time64.md).

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
