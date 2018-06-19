---
title: strtoumax –, _strtoumax_l –, wcstoumax –, _wcstoumax_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wcstoumax_l
- _strtoumax_l
- wcstoumax
- strtoumax
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
- wcstoumax
- _tcstoumax
- _strtoumax_l
- _wcstoumax_l
- _tcstoumax_l
- strtoumax
dev_langs:
- C++
helpviewer_keywords:
- _strtoumax_l function
- conversion functions
- wcstoumax function
- _wcstoumax_l function
- strtoumax function
ms.assetid: 566769f9-495b-4508-b9c6-02217a578897
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0691e26387f70e80718d8af84ba9ff18ad7fd489
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417801"
---
# <a name="strtoumax-strtoumaxl-wcstoumax-wcstoumaxl"></a>strtoumax, _strtoumax_l, wcstoumax, _wcstoumax_l

Převede řetězce na celočíselnou hodnotu typu největší podporovaná celé číslo bez znaménka.

## <a name="syntax"></a>Syntaxe

```C
uintmax_t strtoumax(
   const char *strSource,
   char **endptr,
   int base
);
uintmax_t _strtoumax_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
uintmax_t wcstoumax(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
uintmax_t _wcstoumax_l(
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
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**strtoumax –** vrátí převedenou hodnotu, pokud existuje, nebo **UINTMAX_MAX** na přetečení. **strtoumax –** vrátí hodnotu 0, pokud žádný převod lze provést. **wcstoumax –** vrátí hodnot analogicky na **strtoumax –**. Pro obě funkce **errno** je nastaven na **erange –** případě přetečení nebo podtečení.

Další informace o návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí převede vstupní řetězec *strSource* k **uintmax_t** celočíselnou hodnotu.

**strtoumax –** ukončí čtení řetězce *strSource* u prvního znaku nemůže rozpoznat jako součást číslo. To může být ukončující znak hodnoty null, nebo to může být první číselné znak, který je větší než nebo rovno *základní*. **Lc_numeric –** kategorie nastavení národního prostředí určuje rozpoznávání základ – znak v *strSource*. Další informace najdete v tématu [setlocale _wsetlocale](setlocale-wsetlocale.md). **strtoumax –** a **wcstoumax –** použít aktuální národní prostředí; **_strtoumax_l –** a **_wcstoumax_l –** jsou identické s tím rozdílem, že místo toho používají národní prostředí, je předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavena kontroly je uložený v umístění, které ukazuje *endptr*. Pokud žádný převod lze provést (nebyly nalezeny žádné platné číslice nebo byl zadán neplatný základní), hodnota *strSource* je uložený v umístění, které ukazuje *endptr*.

Široká charakterová verzi **strtoumax –** je **wcstoumax –**; jeho *strSource* je argumentem široká charakterová řetězce. Tyto funkce, jinak hodnota chovají stejně jako.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoumax**|**strtoumax –**|**strtoumax –**|**wcstoumax –**|
|**_tcstoumax_l**|**strtoumax_l**|**_strtoumax_l**|**_wcstoumax_l**|

**strtoumax –** očekává *strSource* tak, aby odkazoval na řetězec v následujícím formátu:

> [*prázdné*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*číslic* &#124; *písmena*]  

A *prázdné* může obsahovat místa a karta znaků, které se mají ignorovat. *číslic* jsou jeden nebo více desetinných míst. *písmena* jsou jeden nebo více znaků 'a' přes 'z' (nebo 'A' až 'Z'). První znak, který se nevejde tento formulář zastaví kontroly. Pokud *základní* mezi 2 a 36, je použita jako základní číslo. Pokud *základní* 0, počáteční znaky řetězce, který ukazuje *strSource* se používají k určení ve znalostní bázi. Pokud je první znak '0' a druhá znak není 'x' nebo 'X', řetězec interpretována jako osmičková celé číslo. Pokud první znak je '0' a druhá znak je písmeno "x" nebo "X", řetězec interpretována jako hexadecimální celé číslo. Pokud je první znak ' 1' přes ' 9', řetězec interpretována jako desítkové celé číslo. Písmena 'a' do 'z' (nebo 'A' až 'Z') jsou přiřazeny hodnoty 10 až 35; pouze písmena, jejichž přiřazené hodnoty jsou menší než *základní* jsou povoleny. První znak mimo rozsah základní zastaví kontroly. Například pokud *základní* je 0 a první znak zkontrolovat je '0', osmičková celé číslo se předpokládá, a znak "8" nebo "9" by zastavit kontroly. **strtoumax –** umožňuje znaménko plus (**+**) nebo minus (**-**) předpona; jako úvodní znaménka minus označuje, že návratová hodnota je dva na doplněk absolutní hodnota převedený řetězec.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtoumax –**|\<stdlib.h>|
|**wcstoumax –**|\<stdlib.h > nebo \<wchar.h >|
|**_strtoumax_l**|\<stdlib.h>|
|**_wcstoumax_l**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [strtod –](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funkce převodu řetězců na numerické hodnoty](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoimax, _strtoimax_l, wcstoimax, _wcstoimax_l](strtoimax-strtoimax-l-wcstoimax-wcstoimax-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
