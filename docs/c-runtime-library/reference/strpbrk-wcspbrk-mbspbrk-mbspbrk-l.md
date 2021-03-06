---
title: strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l
ms.date: 4/2/2020
api_name:
- _mbspbrk
- wcspbrk
- _mbspbrk_l
- strpbrk
- _o__mbspbrk
- _o__mbspbrk_l
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fstrpbrk
- _mbspbrk
- strpbrk
- _tcspbrk
- _ftcspbrk
- wcspbrk
helpviewer_keywords:
- fstrpbrk function
- _ftcspbrk function
- _mbspbrk_l function
- strpbrk function
- _fstrpbrk function
- mbspbrk function
- characters [C++], scanning strings
- _tcspbrk function
- wcspbrk function
- ftcspbrk function
- character sets [C++], scanning strings for characters
- strings [C++], scanning
- tcspbrk function
- _mbspbrk function
- mbspbrk_l function
ms.assetid: 80b504f7-a167-4dde-97ad-4ae3000dc810
ms.openlocfilehash: 507f6b99416cd59c3a0383e3e41a7ae26c44b019
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911184"
---
# <a name="strpbrk-wcspbrk-_mbspbrk-_mbspbrk_l"></a>strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l

Hledá v řetězcích znaky v určených znakových sadách.

> [!IMPORTANT]
> `_mbspbrk`a `_mbspbrk_l` nelze je použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *strpbrk(
   const char *str,
   const char *strCharSet
); // C only
char *strpbrk(
   char *str,
   const char *strCharSet
); // C++ only
const char *strpbrk(
   const char *str,
   const char *strCharSet
); // C++ only
wchar_t *wcspbrk(
   const wchar_t *str,
   const wchar_t *strCharSet
); // C only
wchar_t *wcspbrk(
   wchar_t *str,
   const wchar_t *strCharSet
); // C++ only
const wchar_t *wcspbrk(
   const wchar_t *str,
   const wchar_t *strCharSet
); // C++ only
unsigned char *_mbspbrk(
   const unsigned char *str,
   const unsigned char *strCharSet
); // C only
unsigned char *_mbspbrk(
   unsigned char *str,
   const unsigned char *strCharSet
); // C++ only
const unsigned char *_mbspbrk(
   const unsigned char *str,
   const unsigned char *strCharSet
); // C++ only
unsigned char *_mbspbrk_l(
   const unsigned char *str,
   const unsigned char *strCharSet,
   _locale_t locale
); // C only
unsigned char *_mbspbrk_l(
   unsigned char *str,
   const unsigned char *strCharSet,
   _locale_t locale
); // C++ only
const unsigned char *_mbspbrk_l(
   const unsigned char *str,
   const unsigned char* strCharSet,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*str*<br/>
Hledaný řetězec zakončený hodnotou null.

*strCharSet*<br/>
Znaková sada zakončená hodnotou null

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na první výskyt libovolného znaku z *strCharSet* v *str*nebo na ukazatel s hodnotou null, pokud dva řetězcové argumenty nemají společné znaky.

## <a name="remarks"></a>Poznámky

`strpbrk` Funkce vrací ukazatel na první výskyt znaku v *str* , který patří do sady znaků v *strCharSet*. Hledání nezahrnuje ukončující znak null.

`wcspbrk`a `_mbspbrk` jsou verze s velkým znakem a vícebajtovým znakem `strpbrk`. Argumenty a návratová hodnota `wcspbrk` jsou řetězce s velkým počtem znaků; Ty `_mbspbrk` jsou vícebajtové znakové řetězce.

`_mbspbrk`ověří jeho parametry. Pokud parametr *str* nebo *strCharSet* má hodnotu null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, `_mbspbrk` vrátí hodnotu null a nastaví `errno` na EINVAL. `strpbrk`a `wcspbrk` neověřuje jejich parametry. Tyto tři funkce se chovají identicky jinak.

`_mbspbrk`je podobné jako `_mbscspn` s tím `_mbspbrk` rozdílem, že vrací ukazatel, nikoli hodnotu typu [size_t](../../c-runtime-library/standard-types.md).

V jazyce C tyto funkce přebírají ukazatel **const** pro první argument. V jazyce C++ jsou k dispozici dvě přetížení. Přetížení přebírající ukazatel na **konstantu** vrací ukazatel na **const**; verze, která přebírá ukazatel na jiný typ než**const** , vrací ukazatel na**nekonstantní**hodnotu. _CRT_CONST_CORRECT_OVERLOADS makra je definováno, pokud jsou k dispozici obě verze **const** i non-**const** . Pokud vyžadujete**nekonstantní** chování pro obě přetížení jazyka C++, definujte symbol _CONST_RETURN.

Výstupní hodnota je ovlivněna nastavením LC_CTYPE kategorie národního prostředí; Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md). Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** je shodná s tím rozdílem, že místo toho používá parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcspbrk`|`strpbrk`|`_mbspbrk`|`wcspbrk`|
|**není k dispozici**|**není k dispozici**|`_mbspbrk_l`|**není k dispozici**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`strpbrk`|\<String. h>|
|`wcspbrk`|\<String. h> nebo \<WCHAR. h>|
|`_mbspbrk`, `_mbspbrk_l`|\<Mbstring. h>|

Další informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strpbrk.c

#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[100] = "The 3 men and 2 boys ate 5 pigs\n";
   char *result = NULL;

   // Return pointer to first digit in "string".
   printf( "1: %s\n", string );
   result = strpbrk( string, "0123456789" );
   printf( "2: %s\n", result++ );
   result = strpbrk( result, "0123456789" );
   printf( "3: %s\n", result++ );
   result = strpbrk( result, "0123456789" );
   printf( "4: %s\n", result );
}
```

```Output
1: The 3 men and 2 boys ate 5 pigs

2: 3 men and 2 boys ate 5 pigs

3: 2 boys ate 5 pigs

4: 5 pigs
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strchr, wcschr, _mbschr, _mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
