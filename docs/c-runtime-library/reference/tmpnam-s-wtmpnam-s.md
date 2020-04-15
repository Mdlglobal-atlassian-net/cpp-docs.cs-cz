---
title: tmpnam_s, _wtmpnam_s
ms.date: 4/2/2020
api_name:
- tmpnam_s
- _wtmpnam_s
- _o__wtmpnam_s
- _o_tmpnam_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
ms.openlocfilehash: e34fbe64d342205659a4b0bdaf703248e62ed733
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362414"
---
# <a name="tmpnam_s-_wtmpnam_s"></a>tmpnam_s, _wtmpnam_s

Vygenerujte názvy, které můžete použít k vytvoření dočasných souborů. Jedná se o verze [tmpnam a _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) s vylepšeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t tmpnam_s(
   char * str,
   size_t sizeInChars
);
errno_t _wtmpnam_s(
   wchar_t *str,
   size_t sizeInChars
);
template <size_t size>
errno_t tmpnam_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _wtmpnam_s(
   wchar_t (&str)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Ukazatel, který bude obsahovat generovaný název.

*sizeInChars*<br/>
Velikost vyrovnávací paměti ve znacích.

## <a name="return-value"></a>Návratová hodnota

Obě tyto funkce vrátí 0, pokud je úspěšná nebo číslo chyby při selhání.

### <a name="error-conditions"></a>Chybové stavy

|||||
|-|-|-|-|
|*Str*|*sizeInChars*|**Návratová hodnota**|**Obsah**  *str*|
|**Null**|jakékoli|**EINVAL**|nezměněno|
|není **NULL** (odkazuje na platnou paměť)|příliš krátká|**ERANGE**|nezměněno|

Pokud *str* je **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce nastavit **errno** na **EINVAL** a vrátit **EINVAL**.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí vrátí název souboru, který v současné době neexistuje. **tmpnam_s** vrátí jedinečný název v určeném dočasném adresáři systému Windows vráceném [službou GetTempPathW](/windows/win32/api/fileapi/nf-fileapi-gettemppathw). Poznámka: Než když je název souboru předem pended s zpětným lomítkem a žádné informace o cestě, jako je například \fname21, to znamená, že název je platný pro aktuální pracovní adresář.

Pro **tmpnam_s**můžete tento název generovaného souboru uložit do *str*. Maximální délka řetězce vráceného **tmpnam_s** je **L_tmpnam_s**, definované v STDIO. H. Pokud *str* je **NULL**, **pak tmpnam_s** opustí výsledek vnitřní statické vyrovnávací paměti. Proto všechny následné volání zničit tuto hodnotu. Název generovaný **tmpnam_s** se skládá z programem generovaného názvu souboru a po prvním volání **tmpnam_s**přípony sekvenčních čísel v základu 32 (.1-.1vvvvvvu, když **TMP_MAX_S** v STDIO. H je **INT_MAX**).

**tmpnam_s** podle potřeby automaticky zpracovává argumenty vícebajtových řetězců a rozpozná se sekvence vícebajtových znaků podle znakové stránky OEM získané z operačního systému. **_wtmpnam_s** je širokoznaková verze **tmpnam_s**; argument a vrácená hodnota **_wtmpnam_s** jsou řetězce širokých znaků. **_wtmpnam_s** a **tmpnam_s** se chovají stejně s tím rozdílem, že **_wtmpnam_s** nezpracovává vícebajtové řetězce znaků.

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky, což eliminuje potřebu zadat argument velikosti. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam_s**|**tmpnam_s**|**tmpnam_s**|**_wtmpnam_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**tmpnam_s**|\<stdio.h>|
|**_wtmpnam_s**|\<stdio.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_tmpnam_s.c
// This program uses tmpnam_s to create a unique filename in the
// current working directory.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char name1[L_tmpnam_s];
   errno_t err;
   int i;

   for (i = 0; i < 15; i++)
   {
      err = tmpnam_s( name1, L_tmpnam_s );
      if (err)
      {
         printf("Error occurred creating unique filename.\n");
         exit(1);
      }
      else
      {
         printf( "%s is safe to use as a temporary file.\n", name1 );
      }
   }
}
```

```Output
C:\Users\LocalUser\AppData\Local\Temp\u19q8.0 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.1 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.2 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.3 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.4 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.5 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.6 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.7 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.8 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.9 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.a is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.b is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.c is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.d is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.e is safe to use as a temporary file.
```

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
