---
title: _strdate_s –, _wstrdate_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e4e9ff3783fc7a89e7af42ebf283209c034c0d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414308"
---
# <a name="strdates-wstrdates"></a>_strdate_s, _wstrdate_s

Zkopírujte aktuální systémový datum do vyrovnávací paměti. Toto jsou verze [_strdate –, _wstrdate –](strdate-wstrdate.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Ukazatel do vyrovnávací paměti, který je zadán řetězec formátovaný datum.

*numberOfElements*<br/>
Velikost vyrovnávací paměti.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v kód chyby. H; v tabulce níže najdete přesné chyby generované pomocí této funkce. Další informace o kódy chyb naleznete v tématu [errno](../../c-runtime-library/errno-constants.md).

## <a name="error-conditions"></a>Chybové stavy

|*Vyrovnávací paměti*|*numberOfElements*|Vrátí|Obsah *vyrovnávací paměti*|
|--------------|------------------------|------------|--------------------------|
|**HODNOTU NULL**|(všechny)|**EINVAL –**|nedojde ke změně|
|Není **NULL** (směřující do platné vyrovnávací paměti)|0|**EINVAL –**|nedojde ke změně|
|Není **NULL** (směřující do platné vyrovnávací paměti)|0 < *numberOfElements* < 9|**EINVAL –**|prázdný řetězec.|
|Není **NULL** (směřující do platné vyrovnávací paměti)|*numberOfElements* > = 9|0|Aktuální datum formátu zadaný v poznámkách|

## <a name="security-issues"></a>Problémy se zabezpečením

Předávání v neplatný bez **NULL** hodnota vyrovnávací paměti bude výsledkem narušení přístupu, pokud *numberOfElements* parametr je větší než 9.

Předávání hodnot pro velikost, která je větší než skutečná velikost *vyrovnávací paměti* bude mít za následek přetečení vyrovnávací paměti.

## <a name="remarks"></a>Poznámky

Tyto funkce zajistit bezpečnější verzích **_strdate –** a **_wstrdate –**. **_Strdate_s –** funkce zkopíruje aktuální systémový datum do vyrovnávací paměti, na kterou odkazuje *vyrovnávací paměti*naformátovanou **mm**/**dd** / **rr**, kde **mm** je dvě číslice představující měsíc, **dd** je dvě číslice představující den, a **RR**  je poslední dvě číslice roku. Například řetězec **12/05/99** představuje 5 prosinec 1999. Vyrovnávací paměti musí mít alespoň 9 znaků.

**_wstrdate_s –** je verze široká charakterová **_strdate_s –**; argument a vrátí hodnotu **_wstrdate_s –** jsou široká charakterová řetězce. Tyto funkce chovají stejně jako jinak.

Pokud *vyrovnávací paměti* je **NULL** ukazatele, nebo pokud *numberOfElements* je menší než 9 znaků, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte **errno** k **einval –** Pokud vyrovnávací paměť je **NULL** nebo, pokud *numberOfElements*je menší než nebo rovna 0, nebo sady **errno** k **erange –** Pokud *numberOfElements* je menší než 9.

V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mapping"></a>Mapování obecného textu rutiny:

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s –**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strdate**|\<Time.h >|
|**_wstrdate**|\<Time.h > nebo \<wchar.h >|
|**_strdate_s**|\<Time.h >|

## <a name="example"></a>Příklad

Podívejte se na příklad pro [čas](time-time32-time64.md).

## <a name="see-also"></a>Viz také

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
