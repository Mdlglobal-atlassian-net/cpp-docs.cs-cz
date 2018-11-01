---
title: _strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l
ms.date: 11/04/2016
apiname:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
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
- _mbsnbcnt
- wcsncnt
- _tcsnbcnt
- _mbsnccnt
- _ftcsnbcnt
- mbsnbcnt
- strncnt
- mbsnbcnt_l
- mbsnccnt_l
- mbsnccnt
- _strncnt
- _wcsncnt
helpviewer_keywords:
- _strncnt function
- _mbsnbcnt function
- _mbsnbcnt_l function
- _mbsnccnt_l function
- mbsnbcnt_l function
- mbsnbcnt function
- tcsnbcnt function
- mbsnccnt_l function
- strncnt function
- _tcsnbcnt function
- mbsnccnt function
- wcsncnt function
- _mbsnccnt function
- _wcsncnt function
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
ms.openlocfilehash: 6322f9511f0813eeaeb49383f49c73e361048cd9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573423"
---
# <a name="strncnt-wcsncnt-mbsnbcnt-mbsnbcntl-mbsnccnt-mbsnccntl"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l

Vrátí počet znaků nebo bajtů v rámci zadaného počtu.

> [!IMPORTANT]
> **_mbsnbcnt –**, **_mbsnbcnt_l –**, **_mbsnccnt –**, a **_mbsnccnt_l –** nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
size_t _strncnt(
   const char *str,
   size_t count
);
size_t _wcsncnt(
   const wchar_t *str,
   size_t count
);
size_t _mbsnbcnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnbcnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
size_t _mbsnccnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnccnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);

```

### <a name="parameters"></a>Parametry

*str*<br/>
Řetězec prověřit.

*Počet*<br/>
Počet znaků nebo bajtů, které mají být prověřeny v *str*.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

**_mbsnbcnt –** a **_mbsnbcnt_l –** vrátí počet bajtů nalezených v prvním *počet* vícebajtových znaků *str*. **_mbsnccnt –** a **_mbsnccnt_l –** vrátí počet znaků nalezených v prvním *počet* bajtů *str*. Pokud nebude nalezen znak null před zkoumání *str* byl dokončen, vrátí počet bajtů nebo znaků nalezených před znakem null. Pokud *str* se skládá z méně než *počet* znaků nebo bajtů, vrátí počet znaků nebo bajtů v řetězci. Pokud *počet* je menší než nula, vrátí 0. V předchozích verzích tyto funkce měly návratovou hodnotu typu **int** spíše než **size_t**.

**_strncnt –** vrátí počet znaků v prvním *počet* bajtů jednobajtového řetězce *str*. **_wcsncnt –** vrátí počet znaků v prvním *počet* širokých znaků širokoznakého řetězce *str*.

## <a name="remarks"></a>Poznámky

**_mbsnbcnt –** a **_mbsnbcnt_l –** počet bajtů nalezených v prvním *počet* vícebajtových znaků *str*. **_mbsnbcnt –** a **_mbsnbcnt_l –** nahradit **mtob** a musí být použity místo **mtob**.

**_mbsnccnt –** a **_mbsnccnt_l –** počet znaků nalezených v prvním *počet* bajtů *str*. Pokud **_mbsnccnt –** a **_mbsnccnt_l –** dojde v druhém bajtu dvoubajtové znakové znak null, první bajt bude také považován za hodnotu null a nebude zahrnut do vrácené hodnoty počtu. **_mbsnccnt –** a **_mbsnccnt_l –** nahradit **btom** a musí být použity místo **btom**.

Pokud *str* je **NULL** ukazatel nebo je *počet* je 0, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md), **errno** je nastavena na **EINVAL**, a funkce vrátí 0.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze těchto funkcí bez **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí místo něho předán v. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt –**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|není k dispozici|
|**_wcsncnt**|není k dispozici|není k dispozici|**_mbsnbcnt**|
|**_wcsncnt**|není k dispozici|není k dispozici|**_mbsnccnt**|
|není k dispozici|není k dispozici|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbcnt**|\<Mbstring.h >|
|**_mbsnbcnt_l**|\<Mbstring.h >|
|**_mbsnccnt**|\<Mbstring.h >|
|**_mbsnccnt_l**|\<Mbstring.h >|
|**_strncnt**|\<tchar.h>|
|**_wcsncnt**|\<tchar.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_mbsnbcnt.c

#include  <mbstring.h>
#include  <stdio.h>

int main( void )
{
   unsigned char str[] = "This is a multibyte-character string.";
   unsigned int char_count, byte_count;
   char_count = _mbsnccnt( str, 10 );
   byte_count = _mbsnbcnt( str, 10 );
   if ( byte_count - char_count )
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );
   else
      printf( "The first 10 characters are single-byte.\n");
}
```

### <a name="output"></a>Výstup

```Output
The first 10 characters are single-byte.
```

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
