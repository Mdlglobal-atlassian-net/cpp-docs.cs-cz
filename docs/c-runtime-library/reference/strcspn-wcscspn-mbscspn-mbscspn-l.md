---
title: strcspn –, wcscspn –, _mbscspn –, _mbscspn_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbscspn_l
- wcscspn
- _mbscspn
- strcspn
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
- strcspn
- _mbscspn
- wcscspn
- _ftcscspn
- _tcscspn
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], searching
- ftcscspn function
- strcspn function
- _mbscspn function
- mbscspn_l function
- wcscspn function
- tcscspn function
- _ftcscspn function
- _mbscspn_l function
- mbscspn function
- _tcscspn function
ms.assetid: f73f51dd-b533-4e46-ba29-d05c553708a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e282aa9d796f06e2682278e08dfae4f24b7a65c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="strcspn-wcscspn-mbscspn-mbscspnl"></a>strcspn, wcscspn, _mbscspn, _mbscspn_l

Vrátí index prvního výskytu řetězce, znaku, který patří do sady znaků.

> [!IMPORTANT]
> **_mbschr –** a **_mbschr_l –** nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
size_t strcspn(
   const char *str,
   const char *strCharSet
);
size_t wcscspn(
   const wchar_t *str,
   const wchar_t *strCharSet
);
size_t _mbscspn(
   const unsigned char *str,
   const unsigned char *strCharSet
);
size_t _mbscspn_l(
   const unsigned char *str,
   const unsigned char *strCharSet,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str –*<br/>
Vyhledávaná řetězce ukončené hodnotou Null.

*strCharSet*<br/>
Ukončené hodnotou Null znakovou sadu.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Tyto funkce vrátí index prvního znaku v *str* který se v *strCharSet*. Pokud není k dispozici znaků v *str* v *strCharSet*, pak vrácená hodnota je délka *str*.

Žádnou návratovou hodnotu je vyhrazena indikující chybu.

## <a name="remarks"></a>Poznámky

**wcscspn –** a **_mbscspn –** jsou široká charakterová a vícebajtových znaků verze **strcspn –**. Argumenty **wcscspn –** jsou široká charakterová řetězce; u **_mbscspn –** jsou řetězců vícebajtových znaků.

**_mbscspn –** ověří jeho parametry. Pokud má jedna *str* nebo *strCharSet* je ukazatel s hodnotou null, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, funkce vrátí hodnotu 0 a nastaví je povoleno spuštění **errno** k **einval –**. **strcspn –** a **wcscspn –** neověřují jejich parametrů. Tyto tři funkce chovají stejně jako jinak.

Výstupní hodnota je ovlivňován nastavením **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez **_l** příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí Místo toho předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscspn –**|**strcspn –**|**_mbscspn**|**wcscspn**|
|není k dispozici|není k dispozici|**_mbscspn_l**|není k dispozici|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strcspn –**|\<String.h >|
|**wcscspn**|\<String.h > nebo \<wchar.h >|
|**_mbscspn –**, **_mbscspn_l –**|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strcspn.c

#include <string.h>
#include <stdio.h>

void test( const char * str, const char * strCharSet )
{
   int pos = strcspn( str, strCharSet );
   printf( "strcspn( \"%s\", \"%s\" ) = %d\n", str, strCharSet, pos );
}

int main( void )
{
   test( "xyzbxz", "abc" );
   test( "xyzbxz", "xyz" );
   test( "xyzbxz", "no match" );
   test( "xyzbxz", "" );
   test( "", "abc" );
   test( "", "" );
}
```

```Output
strcspn( "xyzbxz", "abc" ) = 3
strcspn( "xyzbxz", "xyz" ) = 0
strcspn( "xyzbxz", "no match" ) = 6
strcspn( "xyzbxz", "" ) = 6
strcspn( "", "abc" ) = 0
strcspn( "", "" ) = 0
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
