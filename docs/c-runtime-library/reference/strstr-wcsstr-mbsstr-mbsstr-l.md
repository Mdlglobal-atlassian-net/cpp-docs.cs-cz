---
title: strstr, wcsstr, _mbsstr, _mbsstr_l
ms.date: 11/04/2016
apiname:
- _mbsstr
- wcsstr
- _mbsstr_l
- strstr
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: 42e02473e062c3af9524ed432aa163b7574342de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541060"
---
# <a name="strstr-wcsstr-mbsstr-mbsstrl"></a>strstr, wcsstr, _mbsstr, _mbsstr_l

Vrací ukazatel na první výskyt řetězce vyhledávání v řetězci.

> [!IMPORTANT]
> `_mbsstr` a `_mbsstr_l` nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Řetězec zakončený hodnotou Null pro hledání.

*strSearch*<br/>
Řetězec zakončený hodnotou Null pro hledání.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na první výskyt *strSearch* v *str*, nebo hodnota NULL, pokud *strSearch* se nezobrazují v *str*. Pokud *strSearch* odkazuje na řetězec má nulovou délku, funkce vrátí *str*.

## <a name="remarks"></a>Poznámky

`strstr` Funkce vrátí ukazatel na první výskyt *strSearch* v *str*. Hledání nezahrnuje ukončovací znaky null. `wcsstr` je širokoznaká verze `strstr` a `_mbsstr` je vícebajtová znaková verze. Argumenty a vrácené hodnoty `wcsstr` jsou širokoznaké řetězce `_mbsstr` jsou vícebajtové znakové řetězce. `_mbsstr` ověří jeho parametry. Pokud *str* nebo *strSearch* má hodnotu NULL, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud smí provádění pokračovat, `_mbsstr` nastaví `errno` EINVAL a vrátí hodnotu 0. `strstr` a `wcsstr` neověří jejich parametry. Tyto tři funkce chovají identicky jinak.

> [!IMPORTANT]
> Tyto funkce může mít za následek hrozeb od problémem přetečení vyrovnávací paměti. Problémů přetečení vyrovnávací paměti lze použít k útokům systému, protože umožňují spuštění libovolného kódu, což může způsobit neoprávněné zvýšení úrovně oprávnění. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

V jazyce C, tyto funkce přijímají **const** ukazatele pro první argument. V jazyce C++ jsou k dispozici dvě přetížení. Přetížení přijímající ukazatel na **const** vrací ukazatel na **const**; verze, která přijímá ukazatel na jinou hodnotu než**const** vrací ukazatel na jinou hodnotu než **Const**. _CRT_CONST_CORRECT_OVERLOADS – makro je definováno, pokud **const** a jiných-**const** verze těchto funkcí jsou k dispozici. Pokud budete potřebovat non -**const** chování pro obě přetížení C++, definujte symbol _CONST_RETURN.

Výstupní hodnota je ovlivněna nastavením kategorie národního prostředí LC_CTYPE; Další informace najdete v tématu [setlocale _wsetlocale](setlocale-wsetlocale.md). Verze těchto funkcí, které nemají **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; ty, které mají **_l** přípona jsou stejné s tím rozdílem, že místo toho používají Parametr národního prostředí, které je předáno. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|
|**není k dispozici**|**není k dispozici**|`_mbsstr_l`|**není k dispozici**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`strstr`|\<String.h >|
|`wcsstr`|\<String.h > nebo \<wchar.h >|
|`_mbsstr`, `_mbsstr_l`|\<Mbstring.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string::Find](../../standard-library/basic-string-class.md#find)<br/>
