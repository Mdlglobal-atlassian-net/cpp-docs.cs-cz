---
title: strstr, wcsstr, _mbsstr, _mbsstr_l
ms.date: 11/04/2016
api_name:
- _mbsstr
- wcsstr
- _mbsstr_l
- strstr
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fstrstr
- _ftcsstr
- strstr
- wcsstr
- _mbsstr
- _tcsstr
helpviewer_keywords:
- strings [C++], searching
- mbsstr function
- _ftcsstr function
- ftcsstr function
- fstrstr function
- _tcsstr function
- substrings, finding
- mbsstr_l function
- tcsstr function
- _mbsstr function
- wcsstr function
- _fstrstr function
- _mbsstr_l function
- strstr function
ms.assetid: 03d70c3f-2473-45cb-a5f8-b35beeb2748a
ms.openlocfilehash: 8c113e02f308b634b6bcb8aea6e46fc14b9abd92
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946592"
---
# <a name="strstr-wcsstr-_mbsstr-_mbsstr_l"></a>strstr, wcsstr, _mbsstr, _mbsstr_l

Vrací ukazatel na první výskyt hledaného řetězce v řetězci.

> [!IMPORTANT]
> `_mbsstr`a `_mbsstr_l` nelze je použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *strstr(
   const char *str,
   const char *strSearch
); // C only
char *strstr(
   char *str,
   const char *strSearch
); // C++ only
const char *strstr(
   const char *str,
   const char *strSearch
); // C++ only
wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C only
wchar_t *wcsstr(
   wchar_t *str,
   const wchar_t *strSearch
); // C++ only
const wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C++ only
unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C only
unsigned char *_mbsstr(
   unsigned char *str,
   const unsigned char *strSearch
); // C++ only
const unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C++ only
unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C only
unsigned char *_mbsstr_l(
   unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
const unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*str*<br/>
Řetězec zakončený hodnotou null pro hledání.

*strSearch*<br/>
Řetězec zakončený hodnotou null, který má být hledán.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na první výskyt *strSearch* v *str*nebo hodnotu null, pokud se *strSearch* v *str*nezobrazí. Pokud *strSearch* odkazuje na řetězec o nulové délce, funkce vrátí *str*.

## <a name="remarks"></a>Poznámky

Funkce vrátí ukazatel na první výskyt strSearch v *str*. `strstr` Hledání nezahrnuje ukončující znaky null. `wcsstr`je verze `strstr` vícebajtového znaku a `_mbsstr` je verze vícebajtového znaku. Argumenty a návratová hodnota `wcsstr` jsou řetězce `_mbsstr` s velkým počtem znaků. hodnoty jsou vícebajtové znakové řetězce. `_mbsstr`ověří jeho parametry. Pokud parametr *str* nebo *strSearch* má hodnotu null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, `_mbsstr` nastaví `errno` se na EINVAL a vrátí hodnotu 0. `strstr`a `wcsstr` neověřuje jejich parametry. Tyto tři funkce se chovají identicky jinak.

> [!IMPORTANT]
> Tyto funkce mohou způsobit ohrožení proti problému s přetečením vyrovnávací paměti. Problémy přetečení vyrovnávací paměti lze použít k útoku na systém, protože mohou umožňovat spuštění libovolného kódu, což může způsobit neoprávněné zvýšení oprávnění. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

V jazyce C tyto funkce přebírají ukazatel **const** pro první argument. V C++jsou k dispozici dvě přetížení. Přetížení, které přebírá ukazatel na typ **const** vrací ukazatel na **const**; verze, která přebírá ukazatel na jiný typ než**const** , vrací ukazatel na**nekonstantní**hodnotu. Makro _CRT_CONST_CORRECT_OVERLOADS je definováno, pokud jsou k dispozici obě verze **const** i non-**const** . Pokud pro C++ přetížení vyžadujete**nekonstantní** chování, definujte symbol _CONST_RETURN.

Výstupní hodnota je ovlivněna nastavením kategorie národního prostředí LC_CTYPE; Další informace naleznete v tématu [setlocale, _wsetlocale](setlocale-wsetlocale.md). Verze těchto funkcí, které nemají příponu **_l** , používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** jsou stejné s tím rozdílem, že místo toho používají parametr národního prostředí, který je předán. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|
|**není k dispozici**|**není k dispozici**|`_mbsstr_l`|**není k dispozici**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`strstr`|\<String. h >|
|`wcsstr`|\<String. h > nebo \<WCHAR. h >|
|`_mbsstr`, `_mbsstr_l`|\<Mbstring. h >|

Další informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strstr.c

#include <string.h>
#include <stdio.h>

char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int  result;
   printf( "String to be searched:\n   %s\n", string );
   printf( "   %s\n   %s\n\n", fmt1, fmt2 );
   pdest = strstr( string, str );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "%s found at position %d\n", str, result );
   else
      printf( "%s not found\n", str );
}
```

```Output
String to be searched:
   The quick brown dog jumps over the lazy fox
            1         2         3         4         5
   12345678901234567890123456789012345678901234567890

lazy found at position 36
```

## <a name="see-also"></a>Viz také:

[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string::find](../../standard-library/basic-string-class.md#find)<br/>
