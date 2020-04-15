---
title: _strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l
ms.date: 4/2/2020
api_name:
- _strtoui64
- _strtoui64_l
- _wcstoui64
- _wcstoui64_l
- _o__strtoui64
- _o__strtoui64_l
- _o__wcstoui64
- _o__wcstoui64_l
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wcstoui64_l
- strtoui64_l
- wcstoui64
- _wcstoui64
- _strtoui64_l
- strtoui64
- _strtoui64
- wcstoui64_l
helpviewer_keywords:
- _strtoui64_l function
- _wcstoui64_l function
- string conversion, to integers
- wcstoui64_l function
- _strtoui64 function
- _wcstoui64 function
- wcstoui64 function
- strtoui64_l function
- strtoui64 function
ms.assetid: 7fcb537e-4554-4ceb-a5b6-bc09244e72ef
ms.openlocfilehash: f3c5631a34c35ed5f5b74e15dfc4225224215b89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365466"
---
# <a name="_strtoui64-_wcstoui64-_strtoui64_l-_wcstoui64_l"></a>_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l

Převeďte řetězec na nepodepsanou **__int64** hodnotu.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 _strtoui64(
   const char *strSource,
   char **endptr,
   int base
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned __int64 _strtoui64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strSource*<br/>
Řetězec ukončený hodnotou null pro převod.

*endptr*<br/>
Ukazatel na znak, který zastaví skenování.

*base*<br/>
Číslo základny k použití.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**_strtoui64** vrátí hodnotu reprezentovanou v řetězci *strSource*, s výjimkou případů, kdy by reprezentace způsobila přetečení, v takovém případě vrátí **_UI64_MAX**. **_strtoui64** vrátí hodnotu 0, pokud nelze provést žádný převod.

**_UI64_MAX** je definována v LIMITS. H.

Pokud *strSource* je **NULL** nebo *základna* je nenulová a buď menší než 2 nebo větší než 36, **errno** je nastavena na **EINVAL**.

Další informace o těchto a dalších návratových kódech naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Poznámky

Funkce **_strtoui64** převede *strSource* na **nepodepsanou** **__int64**. **_wcstoui64** je širokoznaková verze **_strtoui64**; jeho *argument strSource* je řetězec s širokým znakem. V opačném případě se tyto funkce chovají stejně.

Obě funkce zastavit čtení řetězce *strSource* na první znak, které nelze rozpoznat jako součást čísla. Může se jedná o ukončující znak null nebo první číselný znak větší nebo roven *základně*.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoui64**|**_strtoui64**|**_strtoui64**|**_wstrtoui64**|
|**_tcstoui64_l**|**_strtoui64_l**|**_strtoui64_l**|**_wstrtoui64_l**|

Nastavení kategorie **LC_NUMERIC** aktuálního národního prostředí určuje rozpoznání znaku radix v *strSource*; Další informace naleznete [v tématu setlocale](setlocale-wsetlocale.md). Funkce bez přípony _l používají aktuální národní prostředí; **_strtoui64_l** a **_wcstoui64_l** jsou shodné s odpovídajícími funkcemi bez **_l** přípony s tím rozdílem, že místo toho používají národní prostředí předané. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavil skenování je uložen v umístění odkazuje *endptr*. Pokud nelze provést žádný převod (nebyly nalezeny žádné platné číslice nebo byl zadán neplatný základ), hodnota *strSource* je uložena v umístění, na které se vztahuje *endptr*.

**_strtoui64** očekává *strSource* přejděte na řetězec následujícího formuláře:

> [*mezery*] [{**+** **-**&#124; }] [**0** [{ **x** &#124; **X** }]] [*číslice* &#124; *písmena*]

*Prázdné znaky* se mohou skládat z mezer a znaků tabulátoru, které jsou ignorovány. *číslice* jsou jedna nebo více desetinných míst. *písmena* jsou jedno nebo více písmen "a" přes "z" (nebo "A" až "Z"). První znak, který se nevejde do tohoto formuláře zastaví skenování. Pokud je *základna* mezi 2 a 36, používá se jako základ čísla. Pokud *base* je 0, počáteční znaky řetězce ukázal *strSource* se používají k určení základu. Pokud je první znak 0 a druhý znak není 'x' nebo 'X', řetězec je interpretován jako osmičkové celé číslo. Pokud je první znak '0' a druhý znak je 'x' nebo 'X', řetězec je interpretován jako šestnáctkové celé číslo. Pokud je první znak '1' až '9', řetězec je interpretován jako desítkové celé číslo. Písmenům "a" přes "z" (nebo "A" až "Z") jsou přiřazeny hodnoty 10 až 35; povolena jsou pouze písmena, jejichž přiřazené hodnoty jsou menší než *základní.* První znak mimo rozsah základny zastaví skenování. Pokud je například *základna* 0 a první naskenovaný znak je "0", předpokládá se osmičkové celé číslo a znak "8" nebo "9" zastaví prohledávací číslo.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strtoui64**|\<stdlib.h>|
|**_wcstoui64**|\<stdlib.h> \<nebo wchar.h>|
|**_strtoui64_l**|\<stdlib.h>|
|**_wcstoui64_l**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strtoui64.c
#include <stdio.h>

unsigned __int64 atoui64(const char *szUnsignedInt) {
   return _strtoui64(szUnsignedInt, NULL, 10);
}

int main() {
   unsigned __int64 u = atoui64("18446744073709551615");
   printf( "u = %I64u\n", u );
}
```

```Output
u = 18446744073709551615
```

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funkce řetězec na číselnou hodnotu](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
