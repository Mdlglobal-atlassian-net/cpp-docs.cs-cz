---
title: strtol, wcstol, _strtol_l, _wcstol_l
ms.date: 4/2/2020
api_name:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- _o__strtol_l
- _o__wcstol_l
- _o_strtol
- _o_wcstol
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wcstol_l
- strtol
- _tcstol
- wcstol
- _strtol_l
- _tcstol_l
helpviewer_keywords:
- wcstol function
- wcstol_l function
- _tcstol function
- string conversion, to integers
- tcstol function
- strtol_l function
- _wcstol_l function
- _strtol_l function
- strtol function
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
no-loc:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- LONG_MAX
- LONG_MIN
- errno
- ERANGE
- EINVAL
- LC_NUMERIC
- _tcstol
- _tcstol_l
- localeconv
- setlocale
- _wsetlocale
- strtod
- _strtod_l
- wcstod
- _wcstod_l
- strtoll
- _strtoll_l
- wcstoll
- _wcstoll_l
- strtoul
- _strtoul_l
- wcstoul
- _wcstoul_l
- atof
- _atof_l
- _wtof
- _wtof_l
ms.openlocfilehash: cc54884cd32ffa9118abfb6d46d659125a44262c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912650"
---
# <a name="strtol-wcstol-_strtol_l-_wcstol_l"></a>strtol, wcstol, _strtol_l, _wcstol_l

Převede řetězce na celočíselnou hodnotu typu **Long** .

## <a name="syntax"></a>Syntaxe

```C
long strtol(
   const char *string,
   char **end_ptr,
   int base
);
long wcstol(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long _strtol_l(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long _wcstol_l(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*řetezce*\
Řetězec zakončený hodnotou null pro převod.

*end_ptr*\
Výstupní parametr, který je nastaven tak, aby odkazoval na znak za posledním interpretováným znakem. Ignorováno, pokud **má hodnotu null**.

*základ*\
Číselná základna, která se má použít.

*jazyka*\
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

**strtol**, **wcstol**, **_strtol_l**a **_wcstol_l** vrací hodnotu reprezentovanou v *řetězci*. Vrátí 0, pokud není možné převod. Pokud by reprezentace způsobila přetečení, vrátí **LONG_MAX** nebo **LONG_MIN**.

**errno** je nastavená na **ERANGE** , pokud dojde k přetečení nebo podtečení. Je nastavená na **EINVAL** , pokud má *řetězec* **hodnotu null**. Nebo, pokud *Base* není nula a menší než 2 nebo vyšší než 36. Další informace o **ERANGE**, **EINVAL**a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **strtol**, **wcstol**, **_strtol_l**a **_wcstol_l** převádějí *řetězec* na hodnotu **Long**. Přestanou číst *řetězec* u prvního znaku, který není rozpoznán jako součást čísla. Může se jednat o ukončovací znak null nebo o první alfanumerický znak, který je větší nebo roven *základní*.

**wcstol** a **_wcstol_l** jsou verze **strtol** a **_strtol_l**pro nejrůznější znaky. *Řetězcovým* argumentem je řetězec s velkým znakem. Tyto funkce se chovají stejně jako **strtol** a **_strtol_l** jinak. Nastavení **LC_NUMERIC** kategorie národního prostředí Určuje rozpoznávání znaku základu (zlomkovou značku nebo desetinné čárky) v *řetězci*. Funkce **strtol** a **wcstol** používají aktuální národní prostředí. **_strtol_l** a **_wcstol_l** místo toho používají předané národní prostředí. Další informace naleznete v tématu [setlocale] a [locale](../../c-runtime-library/locale.md).

Pokud *end_ptr* má **hodnotu null**, je ignorována. V opačném případě ukazatel na znak, který zastavil skenování, je uložen v umístění, na které ukazuje *end_ptr*. Převod není možný, pokud nejsou nalezeny žádné platné číslice nebo je zadána neplatná základna. Hodnota *řetězce* je pak uložena v umístění, na které ukazuje *end_ptr*.

**strtol** očekává, že *řetězec* odkazuje na řetězec v následujícím tvaru:

> [*prázdné znaky*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **x** }]] [*alfanumerické znaky*]

Hranaté závorky (`[ ]`) ohraničují volitelné prvky. Složené závorky a svislé pruhové (`{ | }`) obklopující alternativy pro jeden prvek. *prázdný znak* se může skládat z mezer a znaků tabulátoru, které jsou ignorovány. *alfanumerické znaky* jsou desítkové číslice nebo písmena "a" až "z" (nebo "a" až "z"). První znak, který nevyhovuje tomuto formuláři, zastaví kontrolu. Pokud je *základ* mezi 2 a 36, použije se jako základ čísla. Pokud je *základní* hodnota 0, pro určení základu se použijí počáteční znaky řetězce, na který se odkazuje pomocí *řetězce* . Pokud je první znak 0 a druhý znak není x nebo X, řetězec je interpretován jako osmičkové celé číslo. Pokud je první znak "0" a druhý znak je "x" nebo "X", řetězec je interpretován jako hexadecimální celé číslo. Pokud je první znak "1" až "9", řetězec je interpretován jako desítkové celé číslo. Písmenům "a" až "z" (nebo "A" až "Z") jsou přiřazeny hodnoty 10 až 35. Kontrola umožňuje pouze písmena, jejichž hodnoty jsou nižší než *základní*. První znak mimo rozsah základny zastaví skenování. Předpokládejme například, že *řetězec začíná řetězcem* "01". Pokud je *základní* hodnotou 0, skener předpokládá, že se jedná o osmičkové celé číslo. Znak "8" nebo "9" zastaví skenování.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstol**|**strtol**|**strtol**|**wcstol**|
|**_tcstol_l**|**_strtol_l**|**_strtol_l**|**_wcstol_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtol**|\<Stdlib. h>|
|**wcstol**|\<Stdlib. h> nebo \<WCHAR. h>|
|**_strtol_l**|\<Stdlib. h>|
|**_wcstol_l**|\<Stdlib. h> nebo \<WCHAR. h>|

Funkce **_strtol_l** a **_wcstol_l** jsou specifické pro společnost Microsoft, nikoli součástí standardní knihovny jazyka C. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad [strtod](strtod-strtod-l-wcstod-wcstod-l.md)pro.

## <a name="see-also"></a>Viz také

[Převod dat](../data-conversion.md)\
[Jazyka](../locale.md)\
[localeconv](localeconv.md)\
[setlocale, _wsetlocale](setlocale-wsetlocale.md)\
[Funkce řetězců na numerické hodnoty](../string-to-numeric-value-functions.md)\
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)\
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)\
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)\
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)
