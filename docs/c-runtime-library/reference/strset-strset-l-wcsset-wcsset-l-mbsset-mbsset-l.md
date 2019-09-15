---
title: _strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l
ms.date: 11/04/2016
api_name:
- _wcsset
- _mbsset
- _strset_l
- _strset
- _wcsset_l
- _mbsset_l
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsset
- _strset_l
- _mbsset
- _strset
- mbsset_l
- strset_l
- _wcsset
- _ftcsset
- wcsset_l
- _tcsset_l
- _mbsset_l
- _wcsset_l
- _fstrset
- _tcsset
helpviewer_keywords:
- _wcsset_l function
- _tcsset function
- wcsset_l function
- _ftcsset function
- characters [C++], setting
- _strset function
- ftcsset function
- strings [C++], setting characters
- mbsset function
- tcsset_l function
- _fstrset function
- mbsset_l function
- strset_l function
- _wcsset function
- _mbsset function
- _mbsset_l function
- tcsset function
- _strset_l function
- fstrset function
- _tcsset_l function
ms.assetid: c42ded42-2ed9-4f06-a0a9-247ba305473a
ms.openlocfilehash: 7f8674467c0d02143e6edf1e4e95c6ee3e20c4b5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946771"
---
# <a name="_strset-_strset_l-_wcsset-_wcsset_l-_mbsset-_mbsset_l"></a>_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l

Nastaví znaky řetězce na znak. K dispozici jsou bezpečnější verze těchto funkcí; viz [_strset_s, _strset_s_l, _wcsset_s, _wcsset_s_l, _mbsset_s, _mbsset_s_l](strset-s-strset-s-l-wcsset-s-wcsset-s-l-mbsset-s-mbsset-s-l.md).

> [!IMPORTANT]
> **_mbsset** a **_mbsset_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strset(
   char *str,
   int c
);
char *_strset_l(
   char *str,
   int c,
   locale_t locale
);
wchar_t *_wcsset(
   wchar_t *str,
   wchar_t c
);
wchar_t *_wcsset_l(
   wchar_t *str,
   wchar_t c,
   locale_t locale
);
unsigned char *_mbsset(
   unsigned char *str,
   unsigned int c
);
unsigned char *_mbsset_l(
   unsigned char *str,
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Byl nastaven řetězec zakončený hodnotou null.

*c*<br/>
Nastavení znaků.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na upravený řetězec.

## <a name="remarks"></a>Poznámky

Funkce **_strset** nastaví všechny znaky (s výjimkou ukončujícího znaku null) *str* na *c*, převedeno na **char**. **_wcsset** a **_mbsset_l** jsou široké znaky a verze vícebajtových znaků **_strset**a datové typy argumentů a vrácených hodnot se odpovídajícím způsobem liší. Tyto funkce se chovají identicky jinak.

**_mbsset** ověří své parametry. Pokud je *str* ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **_mbsset** vrátí **hodnotu null** a nastaví **errno** na **EINVAL**. **_strset** a **_wcsset** neověřují své parametry.

Výstupní hodnota je ovlivněna nastavením kategorie **LC_CTYPE** národního prostředí; Další informace najdete v tématu [setlocale, _wsetlocale](setlocale-wsetlocale.md) . Verze těchto funkcí jsou identické, s tím rozdílem, že ty, které nemají příponu **_l** , používají aktuální národní prostředí a ty, které mají příponu **_l** , místo toho používají předaný parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

> [!IMPORTANT]
> Tyto funkce můžou být zranitelné vůči hrozbám přetečení vyrovnávací paměti. Přetečení vyrovnávací paměti lze použít pro systémové útoky, protože mohou způsobit neoprávněné zvýšení oprávnění. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsset**|**_strset**|**_mbsset**|**_wcsset**|
|**_tcsset_l**|**_strset_l**|**_mbsset_l**|**_wcsset_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strset**|\<String. h >|
|**_strset_l**|\<tchar.h>|
|**_wcsset**|\<String. h > nebo \<WCHAR. h >|
|**_wcsset_l**|\<tchar.h>|
|**_mbsset**, **_mbsset_l**|\<Mbstring. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strset.c
// compile with: /W3

#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[] = "Fill the string with something.";
   printf( "Before: %s\n", string );
   _strset( string, '*' ); // C4996
   // Note: _strset is deprecated; consider using _strset_s instead
   printf( "After:  %s\n", string );
}
```

```Output
Before: Fill the string with something.
After:  *******************************
```

## <a name="see-also"></a>Viz také:

[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
