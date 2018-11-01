---
title: strncat – _strncat_l, wcsncat –, _wcsncat_l, _mbsncat –, _mbsncat_l –
ms.date: 11/04/2016
apiname:
- strncat
- _strncat_l
- _mbsncat
- _mbsncat_l
- wcsncat
- wcsncat_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcsncat_l
- _wcsncat_l
- _tcsnccat_l
- _mbsncat
- _strncat_l
- strncat
- _tcsnccat
- _mbsncat_l
- _ftcsncat
- wcsncat
- _tcsncat
helpviewer_keywords:
- concatenating strings
- ftcsncat function
- tcsncat_l function
- _tcsnccat_l function
- _tcsncat function
- strncat function
- _ftcsncat function
- mbsncat function
- mbsncat_l function
- strings [C++], appending
- wcsncat function
- tcsnccat function
- tcsnccat_l function
- _tcsnccat function
- string concatenation [C++]
- appending strings
- characters [C++], appending to strings
- _mbsncat function
- _tcsncat_l function
- _mbsncat_l function
- tcsncat function
ms.assetid: de67363b-68c6-4ca5-91e3-478610ad8159
ms.openlocfilehash: 6d44ec9f75ef1c6677c2f6053746592ba6e86382
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574275"
---
# <a name="strncat-strncatl-wcsncat-wcsncatl-mbsncat-mbsncatl"></a>strncat – _strncat_l, wcsncat –, _wcsncat_l, _mbsncat –, _mbsncat_l –

Připojí znaky řetězce. Bezpečnější verze těchto funkcí jsou k dispozici, najdete v článku [strncat_s – _strncat_s_l, wcsncat_s –, _wcsncat_s_l, _mbsncat_s –, _mbsncat_s_l –](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md) .

> [!IMPORTANT]
> **_mbsncat –** a **_mbsncat_l –** nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *strncat(
   char *strDest,
   const char *strSource,
   size_t count
);
wchar_t *wcsncat(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
unsigned char *_mbsncat(
   unsigned char *strDest,
   const unsigned char *strSource,
   size_t count
);
unsigned char *_mbsncat_l(
   unsigned char *strDest,
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
);
template <size_t size>
char *strncat(
   char (&strDest)[size],
   const char *strSource,
   size_t count
); // C++ only
template <size_t size>
wchar_t *wcsncat(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsncat(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsncat_l(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*strDest*<br/>
Řetězec cíle zakončený hodnotou Null.

*strSource*<br/>
Řetězec zakončený hodnotou Null zdroje.

*Počet*<br/>
Počet znaků k připojení.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na cílový řetězec. Žádná návratová hodnota je vyhrazená k indikaci chyby.

## <a name="remarks"></a>Poznámky

**Strncat –** funkce připojí maximálně prvních *počet* znaků *strSource* k *strDest*. Počáteční znak *strSource* přepíše ukončující znak null proměnné *strDest*. Pokud se objeví znak null v *strSource* před *počet* znaky jsou připojeny, **strncat –** připojí všechny znaky z *strSource*, až po znak null. Pokud *počet* je větší než délka *strSource*, délka *strSource* je použito místo *počet*. Ve všech případech je výsledný řetězec je ukončen znakem null. Pokud se kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

> [!IMPORTANT]
> **strncat –** nekontroluje dostatek místa v *strDest*; proto jde o potenciální příčinu přetečení vyrovnávací paměti. Mějte na paměti, která *počet* omezuje počet znaků jsou připojeny; není limit velikosti *strDest*. Podívejte se na téma níže uvedený příklad. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

**wcsncat –** a **_mbsncat –** jsou širokoznaké a vícebajtové verze **strncat –**. Argumenty řetězce a vrácené hodnoty **wcsncat –** jsou širokoznaké řetězce **_mbsncat –** jsou vícebajtové znakové řetězce. Tyto tři funkce chovají identicky jinak.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze těchto funkcí bez **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí místo něho předán v. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V jazyce C++ mají tyto funkce přetížení šablon. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncat –**|**strncat**|**_mbsnbcat**|**wcsncat –**|
|**_tcsncat_l –**|**_strncat_l**|**_mbsnbcat_l**|**_wcsncat_l**|

> [!NOTE]
> **_strncat_l** a **_wcsncat_l** mít žádnou závislost národního prostředí a neměly by být volány přímo. Jsou určeny pro interní použití rozhraním **_tcsncat_l –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strncat**|\<String.h >|
|**wcsncat –**|\<String.h > nebo \<wchar.h >|
|**_mbsncat**|\<Mbstring.h >|
|**_mbsncat_l**|\<Mbstring.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strncat.c
// Use strcat and strncat to append to a string.
#include <stdlib.h>

#define MAXSTRINGLEN 39

char string[MAXSTRINGLEN+1];
// or char *string = malloc(MAXSTRINGLEN+1);

void BadAppend( char suffix[], int n )
{
   strncat( string, suffix, n );
}

void GoodAppend( char suffix[], size_t n )
{
   strncat( string, suffix, __min( n, MAXSTRINGLEN-strlen(string)) );
}

int main( void )
{
   string[0] = '\0';
   printf( "string can hold up to %d characters\n", MAXSTRINGLEN );

   strcpy( string, "This is the initial string!" );
   // concatenate up to 20 characters...
   BadAppend( "Extra text to add to the string...", 20 );
   printf( "After BadAppend :  %s (%d chars)\n", string, strlen(string) );

   strcpy( string, "This is the initial string!" );
   // concatenate up to 20 characters...
   GoodAppend( "Extra text to add to the string...", 20 );
   printf( "After GoodAppend:  %s (%d chars)\n", string, strlen(string) );
}
```

### <a name="output"></a>Výstup

```Output
string can hold up to 39 characters
After BadAppend :  This is the initial string!Extra text to add to (47 chars)
After GoodAppend:  This is the initial string!Extra text t (39 chars)
```

Všimněte si, že **BadAppend** způsobil přetečení vyrovnávací paměti.

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
