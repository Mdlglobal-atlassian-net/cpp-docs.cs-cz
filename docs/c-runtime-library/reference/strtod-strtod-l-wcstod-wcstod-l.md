---
title: "strtod –, _strtod_l –, wcstod –, _wcstod_l – | Microsoft Docs"
ms.custom: 
ms.date: 10/20/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
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
- _tcstod
- strtod
- wcstod
- _strtod_l
- _wcstod_l
- stdlib/strtod
- corecrt_wstdlib/wcstod
- stdlib/_strtod_l
- corecrt_wstdlib/_wcstod_l
dev_langs:
- C++
helpviewer_keywords:
- wcstod_l function
- tcstod_l function
- _tcstod_l function
- strtod function
- _wcstod_l function
- wcstod function
- strtod_l function
- tcstod function
- _tcstod function
- _strtod_l function
- string conversion, to floating point values
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fe18737b52ba2b04e3ee09813c6b48b6ebdf0363
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="strtod-strtodl-wcstod-wcstodl"></a>strtod, _strtod_l, wcstod, _wcstod_l

Převod řetězců na hodnotu dvojitou přesností.

## <a name="syntax"></a>Syntaxe

```C
double strtod(
   const char *nptr,
   char **endptr
);
double _strtod_l(
   const char *nptr,
   char **endptr,
   _locale_t locale
);
double wcstod(
   const wchar_t *nptr,
   wchar_t **endptr
);
double wcstod_l(
   const wchar_t *nptr,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*nptr*  
Řetězce ukončené hodnotou Null pro převod.

*endptr*  
Ukazatel na znak, který zastaví kontroly.

*Národní prostředí*  
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

`strtod` Vrátí hodnotu číslo s plovoucí desetinnou čárkou s výjimkou případů, kdy reprezentace by způsobilo přetečení, ve kterém případ funkce vrátí +/-`HUGE_VAL`. Znaménko `HUGE_VAL` odpovídá znaménko hodnotu, která není možné vyjádřit. `strtod` Vrátí hodnotu 0, pokud žádný převod můžete provést, nebo dojde podtečení.

`wcstod` Vrátí hodnoty analogicky na `strtod`. Pro obě funkce `errno` je nastaven na `ERANGE` Pokud dojde k přetečení nebo podtečení a volána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o tomto a ostatní návratové kódy.

## <a name="remarks"></a>Poznámky

Jednotlivé funkce převede vstupní řetězec *nptr* k `double`. `strtod` Funkce převede *nptr* na hodnotu dvojitou přesností. `strtod` ukončí čtení řetězce *nptr* u prvního znaku nemůže rozpoznat jako součást číslo. To může být ukončující znak hodnoty null. `wcstod` široká charakterová verze `strtod`; jeho *nptr* je argumentem široká charakterová řetězce. Tyto funkce chovají stejně jako jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcstod`|`strtod`|`strtod`|`wcstod`|
|`_tcstod_l`|`_strtod_l`|`_strtod_l`|`_wcstod_l`|

`LC_NUMERIC` Kategorie nastavení aktuální národní prostředí určuje rozpoznávání základ – bod znaku v *nptr*. Další informace najdete v tématu [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). Funkce bez `_l` příponu použít aktuální národní prostředí; `_strtod_l` je stejný jako `_strtod_l` s tím rozdílem, že se používají *národního prostředí* předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není `NULL`, ukazatel na znak, který zastavena kontroly je uložený v umístění, na kterou odkazuje *endptr*. Pokud žádný převod lze provést (nebyly nalezeny žádné platné číslice nebo byl zadán neplatný základní), hodnota *nptr* je uložený v umístění, na kterou odkazuje *endptr*.

`strtod` očekává *nptr* tak, aby odkazoval na řetězec jednoho z následujících podob:

[*whitespace*] [*sign*] {*digits* [*radix* *digits*] &#124; *radix* *digits*} [{**e** &#124; **E**} [*sign*] *digits*]  
[*whitespace*] [*sign*] {**0x** &#124; **0X**} {*hexdigits* [*radix* *hexdigits*] &#124; *radix* *hexdigits*} [{**p** &#124; **P**} [*sign*] *hexdigits*]  
[*whitespace*] [*sign*] {**INF** &#124; **INFINITY**}  
[*whitespace*] [*sign*] **NAN** [*sequence*]

Volitelné úvodního *prázdné* může obsahovat místa a karta znaků, které se mají ignorovat; *přihlašovací* je buď plus (+) nebo minus (-); *číslic* jsou jeden nebo více desetinných míst; *hexdigits* jsou jeden nebo více šestnáctkové číslice; *základ –* je základ – bod znak, buď tečkou (.) v výchozí národní prostředí "C", nebo národní prostředí – konkrétní hodnotu aktuální národní prostředí je jiné, nebo když *národního prostředí* je zadán; *pořadí* je posloupnost alfanumerické znaky nebo podtržítka. Ve formulářích decimal i hexadecimální číslo žádné číslic se zobrazí před bod je základ – znak alespoň jeden musí být uvedena za základ – znak bodu. Ve formuláři, decimal, může následovat desetinných míst exponent, který se skládá z úvodní písmeno (**e** nebo **E**) a volitelně znaménkem. V šestnáctkovém formátu může následovat šestnáctkové číslice exponentem, který se skládá z úvodní písmeno (**p** nebo **P**) a volitelně podepsaný hexadecimální číslo, které představuje exponent jako druhou mocninou 2. V jakémkoli tvaru Pokud se zobrazí exponentu část ani znak základ – bod, bod znak základ – se předpokládá, podle poslední číslice v řetězci. V obou se ignoruje velikost písmen **INF** a **NAN** formulářů. První znak, který neodpovídá jedné z těchto podob zastaví kontroly.

Verze UCRT tyto funkce nepodporuje převod Fortran stylu (**d** nebo **D**) exponentu písmena. Toto nestandardní rozšíření byl podporován ve starších verzích CRT a může být narušující změně kódu. Verze UCRT podporovat hexadecimálními řetězci a odezvy INF a NAN hodnoty, které nejsou podporované v dřívějších verzích. Také to může způsobit dodatečné změny v kódu. Například by řetězec "0x1a" interpretovat `strtod` jako 0,0 v předchozích verzích, ale jako 26.0 ve verzi UCRT.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`strtod`, `_strtod_l`|C: &lt;stdlib.h > C++: &lt;cstdlib – > nebo &lt;stdlib.h > |
|`wcstod`, `_wcstod_l`|C: &lt;stdlib.h > nebo &lt;wchar.h > C++: &lt;cstdlib – >, &lt;stdlib.h > nebo &lt;wchar.h > |

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strtod.c
// This program uses strtod to convert a
// string to a double-precision value; strtol to
// convert a string to long integer values; and strtoul
// to convert a string to unsigned long-integer values.
//

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char   *string, *stopstring;
   double x;
   long   l;
   int    base;
   unsigned long ul;

   string = "3.1415926This stopped it";
   x = strtod( string, &stopstring );
   printf( "string = %s\n", string );
   printf("   strtod = %f\n", x );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "-10110134932This stopped it";
   l = strtol( string, &stopstring, 10 );
   printf( "string = %s\n", string );
   printf("   strtol = %ld\n", l );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "10110134932";
   printf( "string = %s\n", string );

   // Convert string using base 2, 4, and 8:
   for( base = 2; base <= 8; base *= 2 )
   {
      // Convert the string:
      ul = strtoul( string, &stopstring, base );
      printf( "   strtol = %ld (base %d)\n", ul, base );
      printf( "   Stopped scan at: %s\n", stopstring );
   }
}
```

```Output
string = 3.1415926This stopped it
   strtod = 3.141593
   Stopped scan at: This stopped it

string = -10110134932This stopped it
   strtol = -2147483648
   Stopped scan at: This stopped it

string = 10110134932
   strtol = 45 (base 2)
   Stopped scan at: 34932
   strtol = 4423 (base 4)
   Stopped scan at: 4932
   strtol = 2134108 (base 8)
   Stopped scan at: 932
```

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)   
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
[Národní prostředí](../../c-runtime-library/locale.md)   
[Funkce řetězců na číselné hodnoty](../../c-runtime-library/string-to-numeric-value-functions.md)   
[strtol –, wcstol –, _strtol_l –, _wcstol_l –](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
[strtoul –, _strtoul_l –, wcstoul –, _wcstoul_l –](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
[atof, _atof_l, _wtof, _wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
[localeconv –](../../c-runtime-library/reference/localeconv.md)   
[_create_locale, _wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
[_free_locale](../../c-runtime-library/reference/free-locale.md)