---
title: _strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l
ms.date: 4/2/2020
api_name:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
- _o__mbsnbcnt
- _o__mbsnbcnt_l
- _o__mbsnccnt
- _o__mbsnccnt_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 020b844d884182ae7553fec9e9db746987189910
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914213"
---
# <a name="_strncnt-_wcsncnt-_mbsnbcnt-_mbsnbcnt_l-_mbsnccnt-_mbsnccnt_l"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l

Vrátí počet znaků nebo bajtů v zadaném počtu.

> [!IMPORTANT]
> **_mbsnbcnt**, **_mbsnbcnt_l**, **_mbsnccnt**a **_mbsnccnt_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Řetězec, který se má prozkoumat

*výpočtu*<br/>
Počet znaků nebo bajtů, které se mají prozkoumat v *str*.

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

**_mbsnbcnt** a **_mbsnbcnt_l** vrací počet bajtů nalezených v prvním *počtu* vícebajtových znaků *str*. **_mbsnccnt** a **_mbsnccnt_l** vrátí počet znaků nalezených v prvním *počtu* bajtů *str*. Pokud se před dokončením vyhodnocení *str* objevil znak null, vrátí počet bajtů nebo znaků nalezených před znakem null. Pokud se *str* skládá z menšího počtu znaků nebo bajtů, vrátí *počet znaků nebo* bajtů v řetězci. Pokud je *počet* menší než nula, vrátí 0. V předchozích verzích měly tyto funkce vrácenou hodnotu typu **int** místo **size_t**.

**_strncnt** vrátí počet znaků v prvním *počtu* bajtů *str*řetězce s jedním bajtem. **_wcsncnt** vrátí počet znaků v první řadě znaků *v řetězci řetězce*s velkým *počtem* znaků.

## <a name="remarks"></a>Poznámky

**_mbsnbcnt** a **_mbsnbcnt_l** spočítá počet bajtů nalezených v prvním *počtu* vícebajtových znaků *str*. **_mbsnbcnt** a **_mbsnbcnt_l** nahrazují **mtob** a měly by se používat místo **mtob**.

**_mbsnccnt** a **_mbsnccnt_l** spočítá počet znaků nalezených v prvním *počtu* bajtů *str*. Pokud **_mbsnccnt** a **_mbsnccnt_l** v druhém bajtu dvoubajtového znaku nalezne znak null, první bajt je také považován za null a není zahrnut do hodnoty vráceného počtu. **_mbsnccnt** a **_mbsnccnt_l** nahrazují **Btom** a měly by se používat místo **Btom**.

Pokud *je str* ukazatel **s hodnotou null** nebo je *počet* 0, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md), **errno** je nastaveno na **EINVAL**a funkce vrátí 0.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** kategorie národního prostředí; Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md) . Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|neuvedeno|
|**_wcsncnt**|neuvedeno|neuvedeno|**_mbsnbcnt**|
|**_wcsncnt**|neuvedeno|neuvedeno|**_mbsnccnt**|
|neuvedeno|neuvedeno|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbcnt**|\<Mbstring. h>|
|**_mbsnbcnt_l**|\<Mbstring. h>|
|**_mbsnccnt**|\<Mbstring. h>|
|**_mbsnccnt_l**|\<Mbstring. h>|
|**_strncnt**|\<Tchar. h>|
|**_wcsncnt**|\<Tchar. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
