---
title: strtoll –, _strtoll_l –, wcstoll –, _wcstoll_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- strtoll
- wcstoll
- _strtoll_l
- _wcstoll_l
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strtoll_l
- _tcstoll_l
- _tcstoll
- _wcstoll_l
- strtoll
- wcstoll
dev_langs:
- C++
helpviewer_keywords:
- _tcstoll_l function
- _wcstoll_l function
- strtoll function
- wcstoll function
- _tcstoll function
- _strtoll_l function
ms.assetid: e2d05dcf-d3b2-4291-9e60-dee77e540fd7
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9138ec6a298c302446077a2c071aef659c9a0ccb
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="strtoll-strtolll-wcstoll-wcstolll"></a>strtoll, _strtoll_l, wcstoll, _wcstoll_l

Převede řetězec na **dlouho** **dlouho** hodnotu.

## <a name="syntax"></a>Syntaxe

```C
long long strtoll(
   const char *strSource,
   char **endptr,
   int base
);
long long wcstoll(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
long long _strtoll_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
long long _wcstoll_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strSource*<br/>
Řetězce ukončené hodnotou Null pro převod.

*endptr*<br/>
Ukazatel na znak, který zastaví kontroly.

*base*<br/>
Číslo základní k použití.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**strtoll –** vrátí hodnotu, která je reprezentována v řetězci *strSource*, s výjimkou případů, kdy reprezentace by způsobilo přetečení – v takovém případě vrátí **LLONG_MAX** nebo **LLONG_MIN**. Funkce vrátí hodnotu 0, pokud žádný převod lze provést. **wcstoll –** vrátí hodnot analogicky na **strtoll –**.

**LLONG_MAX** a **LLONG_MIN** jsou definovány v omezení. H.

Pokud *strSource* je **NULL** nebo *základní* nenulový a je menší než 2 nebo vyšší než 36, **errno** je nastaven na **einval –** .

Další informace o návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**Strtoll –** funkce převede *strSource* k **dlouho** **dlouho**. Obě funkce Zastavit čtení řetězec *strSource* u prvního znaku nemůže rozpoznat jako součást číslo. To může být ukončující znak hodnoty null, nebo to může být první číselné znak, který je větší než nebo rovno *základní*. **wcstoll –** je verze široká charakterová **strtoll –**; jeho *strSource* je argumentem široká charakterová řetězce. Tyto funkce, jinak hodnota chovají stejně jako.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoll –**|**strtoll –**|**strtoll –**|**wcstoll –**|
|**_tcstoll_l –**|**_strtoll_l**|**_strtoll_l**|**_wcstoll_l**|

Jako národní prostředí **lc_numeric –** kategorie nastavení určuje rozpoznávání základ – znak v *strSource*; Další informace najdete v tématu [setlocale _wsetlocale](setlocale-wsetlocale.md). Funkce, které nemají **_l** příponu použít aktuální národní prostředí; **_strtoll_l –** a **_wcstoll_l –** jsou stejné jako odpovídající funkce, které nemají příponu, s tím rozdílem, že místo toho používají národní prostředí, je předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavena kontroly je uložený v umístění, které ukazuje *endptr*. Pokud žádný převod lze provést (nebyly nalezeny žádné platné číslice nebo byl zadán neplatný základní), hodnota *strSource* je uložený v umístění, které ukazuje *endptr*.

**strtoll –** očekává *strSource* tak, aby odkazoval na řetězec v následujícím formátu:

> [*prázdné*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*číslic* &#124; *písmena*]  

A *prázdné* může obsahovat místa a karta znaků, které se mají ignorovat; *číslic* jsou jeden nebo více desetinných míst; *písmena* jsou jeden nebo více znaků 'a' přes 'z' (nebo 'A' až 'Z'). První znak, který se nevejde tento formulář zastaví kontroly. Pokud *základní* mezi 2 a 36, je použita jako základní číslo. Pokud *základní* 0, počáteční znaky řetězce, který ukazuje *strSource* se používají k určení ve znalostní bázi. Pokud je první znak '0' a druhá znak není 'x' nebo 'X', řetězec interpretována jako osmičková celé číslo. Pokud první znak je '0' a druhá znak je písmeno "x" nebo "X", řetězec interpretována jako hexadecimální celé číslo. Pokud je první znak ' 1' přes ' 9', řetězec interpretována jako desítkové celé číslo. Písmena 'a' do 'z' (nebo 'A' až 'Z') jsou přiřazeny hodnoty 10 až 35; pouze písmena, jejichž přiřazené hodnoty jsou menší než *základní* jsou povoleny. První znak mimo rozsah základní zastaví kontroly. Například pokud *základní* je 0 a první znak zkontrolovat je '0', osmičková celé číslo se předpokládá, a znak "8" nebo "9" zastaví kontroly.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtoll –**, **_strtoll_l –**|\<stdlib.h>|
|**wcstoll –**, **_wcstoll_l –**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funkce převodu řetězců na numerické hodnoty](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
