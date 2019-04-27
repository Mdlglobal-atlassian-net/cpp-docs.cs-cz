---
title: _strdate_s, _wstrdate_s
ms.date: 11/04/2016
apiname:
- _strdate_s
- _wstrdate_s
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 85c9ab7dcad68f3aa4832236461cd38b07d4ae44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353986"
---
# <a name="strdates-wstrdates"></a>_strdate_s, _wstrdate_s

Zkopírujte aktuálního systémového data do vyrovnávací paměti. Jde o verzích [_strdate – _wstrdate –](strdate-wstrdate.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Vyrovnávací paměti*<br/>
Ukazatel do vyrovnávací paměti, které se vyplní řetězec formátovaná data.

*numberOfElements*<br/>
Velikost vyrovnávací paměti.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v ERRNO. H. v tabulce níže najdete přesné chyb generovaných touto funkcí. Další informace o chybových kódech naleznete v tématu [errno](../../c-runtime-library/errno-constants.md).

## <a name="error-conditions"></a>Chybové podmínky

|*Vyrovnávací paměti*|*numberOfElements*|Vrátí|Obsah *vyrovnávací paměti*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|(žádné)|**EINVAL**|Nezměněno|
|Není **NULL** (odkazuje na platnou vyrovnávací paměť)|0|**EINVAL**|Nezměněno|
|Není **NULL** (odkazuje na platnou vyrovnávací paměť)|0 < *numberOfElements* < 9|**EINVAL**|Prázdný řetězec|
|Není **NULL** (odkazuje na platnou vyrovnávací paměť)|*numberOfElements* > = 9|0|Aktuální datum ve formátu podle poznámky|

## <a name="security-issues"></a>Problémy se zabezpečením

Předání neplatný bez **NULL** hodnota vyrovnávací paměti se vést k narušení přístupu-li *numberOfElements* parametr je větší než 9.

Předávání hodnot pro velikost, která je větší než skutečná velikost *vyrovnávací paměti* způsobí přetečení vyrovnávací paměti.

## <a name="remarks"></a>Poznámky

Poskytují bezpečnější verze těchto funkcí **_strdate –** a **_wstrdate –**. **_Strdate_s –** funkce zkopíruje aktuálního systémového data do vyrovnávací paměti, na které odkazuje *vyrovnávací paměti*naformátovanou **mm**/**dd** / **rr**, kde **mm** je dvě číslice představující měsíc, **dd** je dvě číslice představující den, a **RR**  je poslední dvě číslice v roce. Například řetězec **12/05/99** představuje 5. prosince 1999. Vyrovnávací paměť musí být alespoň 9 znaků.

**_wstrdate_s –** je verze širokého znaku **_strdate_s –**; argument a návratová hodnota funkce **_wstrdate_s –** jsou širokoznaké řetězce. Tyto funkce chovají identicky jinak.

Pokud *vyrovnávací paměti* je **NULL** ukazatele, nebo pokud *numberOfElements* je menší než 9 znaků, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a nastaví **errno** k **EINVAL** Pokud vyrovnávací paměť je **NULL** nebo, pokud *numberOfElements*je menší než nebo rovno 0, nebo sadu **errno** k **ERANGE** Pokud *numberOfElements* je menší než 9.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky (tím eliminuje nutnost zadat argument velikosti) a dokážou automaticky nahradit starší, nezabezpečené funkce jejími novějšími, zabezpečené protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mapping"></a>Mapování obecného textu rutiny:

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<Time.h > nebo \<wchar.h >|
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
