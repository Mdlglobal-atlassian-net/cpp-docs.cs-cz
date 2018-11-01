---
title: _strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l
ms.date: 11/04/2016
apiname:
- _strlwr_l
- _strlwr
- _wcslwr_l
- _mbslwr_l
- _wcslwr
- _mbslwr
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
apitype: DLLExport
f1_keywords:
- _strlwr
- wcslwr_l
- _ftcslwr
- mbslwr_l
- _mbslwr
- _wcslwr
- strlwr_l
- _tcslwr
- mbslwr
helpviewer_keywords:
- tcslwr function
- _strlwr function
- converting case
- string conversion [C++], case
- mbslwr function
- _strlwr_l function
- strlwr_l function
- _wcslwr function
- ftcslwr function
- strings [C++], case
- _tcslwr_l function
- _wcslwr_l function
- wcslwr_l function
- mbslwr_l function
- tcslwr_l function
- _tcslwr function
- converting case, CRT functions
- _ftcslwr function
- _mbslwr function
- case, converting
- strings [C++], converting case
- _mbslwr_l function
ms.assetid: d279181d-2e7d-401f-ab44-6e7c2786a046
ms.openlocfilehash: a442afd0ede8d9c6e892f50c12153b22f80733b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505687"
---
# <a name="strlwr-wcslwr-mbslwr-strlwrl-wcslwrl-mbslwrl"></a>_strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l

Převede řetězec na malá písmena. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [_strlwr_s – _strlwr_s_l –, _mbslwr_s –, _mbslwr_s_l –, _wcslwr_s –, _wcslwr_s_l –](strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md).

> [!IMPORTANT]
> **_mbslwr –** a **_mbslwr_l –** nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strlwr(
   char * str
);
wchar_t *_wcslwr(
   wchar_t * str
);
unsigned char *_mbslwr(
   unsigned char * str
);
char *_strlwr_l(
   char * str,
   _locale_t locale
);
wchar_t *_wcslwr_l(
   wchar_t * str,
   _locale_t locale
);
unsigned char *_mbslwr_l(
   unsigned char * str,
   _locale_t locale
);
template <size_t size>
char *_strlwr(
   char (&str)[size]
); // C++ only
template <size_t size>
wchar_t *_wcslwr(
   wchar_t (&str)[size]
); // C++ only
template <size_t size>
unsigned char *_mbslwr(
   unsigned char (&str)[size]
); // C++ only
template <size_t size>
char *_strlwr_l(
   char (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
wchar_t *_wcslwr_l(
   wchar_t (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
unsigned char *_mbslwr_l(
   unsigned char (&str)[size],
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*str*<br/>
Řetězec zakončený hodnotou Null pro převod na malá písmena.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na převedený řetězec. Vzhledem k tomu, že změna se provádí na místě, vrácený ukazatel je stejný jako ukazatel předaný jako vstupní argument. Žádná návratová hodnota je vyhrazená k indikaci chyby.

## <a name="remarks"></a>Poznámky

**_Strlwr** funkce převede všechna velká písmena v *str* na malá písmena, počítáno od **LC_CTYPE** nastavením kategorie národního prostředí. Jiné znaky nejsou ovlivněny. Další informace o **LC_CTYPE**, naleznete v tématu [setlocale](setlocale-wsetlocale.md). Verze těchto funkcí bez **_l** používají aktuální národní prostředí pro své chování závislé na národním prostředí; verze s **_l** přípona jsou stejné s tím rozdílem, že používají Předaný parametr národního prostředí Místo toho. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

**_Wcslwr –** a **_mbslwr –** jsou širokoznaké a vícebajtové verze funkce **_strlwr**. Argument a návratová hodnota funkce **_wcslwr –** jsou širokoznaké řetězce **_mbslwr –** jsou vícebajtové znakové řetězce. Tyto tři funkce chovají identicky jinak.

Pokud *str* je **NULL** vyvolána ukazatel, obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud smí provádění pokračovat, tyto funkce vrátí původní řetězec a nastaví **errno** k **EINVAL**.

V jazyce C++ mají tyto funkce přetížení šablon, která vyvolávají novější, zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcslwr –**|**_strlwr**|**_mbslwr**|**_wcslwr**|
|**_tcslwr_l –**|**_strlwr_l**|**_mbslwr_l**|**_wcslwr_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strlwr**, **_strlwr_l –**|\<String.h >|
|**_wcslwr –**, **_wcslwr_l –**|\<String.h > nebo \<wchar.h >|
|**_mbslwr –**, **_mbslwr_l –**|\<Mbstring.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strlwr.c
// compile with: /W3
// This program uses _strlwr and _strupr to create
// uppercase and lowercase copies of a mixed-case string.
#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[100] = "The String to End All Strings!";
   char * copy1 = _strdup( string ); // make two copies
   char * copy2 = _strdup( string );

   _strlwr( copy1 ); // C4996
   // Note: _strlwr is deprecated; consider using _strlwr_s instead
   _strupr( copy2 ); // C4996
   // Note: _strupr is deprecated; consider using _strupr_s instead

   printf( "Mixed: %s\n", string );
   printf( "Lower: %s\n", copy1 );
   printf( "Upper: %s\n", copy2 );

   free( copy1 );
   free( copy2 );
}
```

```Output
Mixed: The String to End All Strings!
Lower: the string to end all strings!
Upper: THE STRING TO END ALL STRINGS!
```

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr](strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)<br/>
