---
title: strtoul –, _strtoul_l –, wcstoul –, _wcstoul_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wcstoul_l
- _strtoul_l
- strtoul
- wcstoul
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
- strtoul
- _tcstoul
- wcstoul
dev_langs:
- C++
helpviewer_keywords:
- _wcstoul_l function
- _tcstoul function
- _strtoul_l function
- string conversion, to integers
- wcstoul function
- strtoul function
- wcstoul_l function
- strtoul_l function
- tcstoul function
ms.assetid: 38f2afe8-8178-4e0b-8bbe-d5c6ad66e3ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 341d331d7de675588524a20596b7ebcd27358b5a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="strtoul-strtoull-wcstoul-wcstoull"></a>strtoul, _strtoul_l, wcstoul, _wcstoul_l

Převod řetězců na nepodepsané dlouho celočíselnou hodnotu.

## <a name="syntax"></a>Syntaxe

```C
unsigned long strtoul(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long _strtoul_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long wcstoul(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long _wcstoul_l(
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

**strtoul –** vrátí převedenou hodnotu, pokud existuje, nebo **ulong_max –** na přetečení. **strtoul –** vrátí hodnotu 0, pokud žádný převod lze provést. **wcstoul –** vrátí hodnot analogicky na **strtoul –**. Pro obě funkce **errno** je nastaven na **erange –** případě přetečení nebo podtečení.

V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o tomto a dalších návratové kódy.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí převede vstupní řetězec *strSource* k **nepodepsané** **dlouho**.

**strtoul –** ukončí čtení řetězce *strSource* u prvního znaku nemůže rozpoznat jako součást číslo. To může být ukončující znak hodnoty null, nebo to může být první číselné znak větší než nebo rovna hodnotě *základní*. **Lc_numeric –** kategorie nastavení národního prostředí určuje rozpoznávání základ – znak v *strSource*; Další informace najdete v tématu [setlocale](setlocale-wsetlocale.md). **strtoul –** a **wcstoul –** použít aktuální národní prostředí; **_strtoul_l –** a **_wcstoul_l –** jsou identické s tím rozdílem, že používají místo předaná národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavena kontroly je uložený v umístění, na kterou odkazuje *endptr*. Pokud žádný převod lze provést (nebyly nalezeny žádné platné číslice nebo byl zadán neplatný základní), hodnota *strSource* je uložený v umístění, na kterou odkazuje *endptr*.

**wcstoul –** je verze široká charakterová **strtoul –**; jeho *strSource* je argumentem široká charakterová řetězce. V opačném případě se tyto funkce chovají stejně jako.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoul –**|**strtoul –**|**strtoul –**|**wcstoul –**|
|**_tcstoul_l**|**strtoul_l –**|**_strtoul_l**|**_wcstoul_l**|

**strtoul –** očekává *strSource* tak, aby odkazoval na řetězec v následujícím formátu:

> [*prázdné*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*číslic* &#124; *písmena*]  

A *prázdné* může obsahovat místa a karta znaků, které se mají ignorovat. *číslic* jsou jeden nebo více desetinných míst. *písmena* jsou jeden nebo více znaků 'a' přes 'z' (nebo 'A' až 'Z'). První znak, který se nevejde tento formulář zastaví kontroly. Pokud *základní* mezi 2 a 36, je použita jako základní číslo. Pokud *základní* 0, počáteční znaky řetězce, na kterou odkazuje *strSource* se používají k určení ve znalostní bázi. Pokud první znak je 0 a druhý znak není 'x' nebo 'X', řetězec interpretována jako osmičková celé číslo. Pokud první znak je '0' a druhá znak je písmeno "x" nebo "X", řetězec interpretována jako hexadecimální celé číslo. Pokud je první znak ' 1' přes ' 9', řetězec interpretována jako desítkové celé číslo. Písmena 'a' do 'z' (nebo 'A' až 'Z') jsou přiřazeny hodnoty 10 až 35; pouze písmena, jejichž přiřazené hodnoty jsou menší než *základní* jsou povoleny. První znak mimo rozsah základní zastaví kontroly. Například pokud *základní* je 0 a první znak zkontrolovat je '0', osmičková celé číslo se předpokládá, a znak "8" nebo "9" zastaví kontroly. **strtoul –** umožňuje znaménkem plus (**+**) nebo minus (**-**) přihlašovací předpony – úvodní znaménka minus označuje, že je Negované návratovou hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtoul –**|\<stdlib.h>|
|**wcstoul –**|\<stdlib.h > nebo \<wchar.h >|
|**_strtoul_l**|\<stdlib.h>|
|**_wcstoul_l**|\<stdlib.h > nebo \<wchar.h >|

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
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
