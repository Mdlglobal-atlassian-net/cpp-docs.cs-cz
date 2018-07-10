---
title: strstr –, wcsstr –, _mbsstr –, _mbsstr_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cbb937cfdce7ed933c637cb48d370515134b66dd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415706"
---
# <a name="strstr-wcsstr-mbsstr-mbsstrl"></a>strstr, wcsstr, _mbsstr, _mbsstr_l
Vrací ukazatel na první výskyt řetězec pro vyhledávání v řetězci.

> [!IMPORTANT]
> **_mbsstr –** a **_mbsstr_l –** nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*str –*<br/>
Řetězce ukončené hodnotou Null pro vyhledávání.

*strSearch*<br/>
Řetězce ukončené hodnotou Null pro vyhledávání.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na první výskyt *strSearch* v *str*, nebo **NULL** Pokud *strSearch* nezobrazí v *str* . Pokud *strSearch* odkazuje na řetězec nulové délky, funkce vrátí hodnotu *str*.

## <a name="remarks"></a>Poznámky

**Strstr –** funkce vrací ukazatel na první výskyt *strSearch* v *str*. Hledání nezahrnuje ukončení znaky null. **wcsstr –** je verze široká charakterová **strstr –** a **_mbsstr –** je verze vícebajtových znaků. Argumenty a vrací hodnotu **wcsstr –** jsou široká charakterová řetězce; u **_mbsstr –** jsou řetězců vícebajtových znaků. **_mbsstr –** ověří jeho parametry. Pokud *str* nebo *strSearch* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud chcete pokračovat, je povoleno spuštění **_mbsstr –** nastaví **errno** k **einval –** a vrátí hodnotu 0. **strstr –** a **wcsstr –** neověřují jejich parametrů. Tyto tři funkce chovají stejně jako jinak.

> [!IMPORTANT]
> Tato funkce může způsobit ohrožení z problému přetečení vyrovnávací paměti. Problémy přetečení vyrovnávací paměti lze použít k útokům systému, protože umožňují provádění libovolný kód, který může způsobit, že bude vyplacena neoprávněně zvýšení úrovně oprávnění. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).

V jazyce C, proveďte tyto funkce ** const ** pro první argument ukazatel. V jazyce C++ jsou k dispozici dva přetížení. Přetížení, které přijímá ukazatel na ** const ** vrací ukazatel na **const **; na verzi, která přebírá ukazatel na jinou hodnotu než**const ** vrací ukazatel na jinou hodnotu než**const **. Makro **_CRT_CONST_CORRECT_OVERLOADS** je definována, pokud obě **const ** a jiných-** const ** verze tyto funkce jsou k dispozici. Pokud budete potřebovat jinou hodnotu než**const ** chování pro obě přetížení C++ definujte symbol **_CONST_RETURN**.

Výstupní hodnota je ovlivňován nastavení národního prostředí kategorie **LC_CTYPE –**; Další informace najdete v tématu [setlocale _wsetlocale](setlocale-wsetlocale.md). Verze tyto funkce, které nemají **_l** příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze, které mají **_l** příponu jsou shodné s tím rozdílem, že místo toho používají Parametr národního prostředí, který se předává v. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsstr –**|**strstr –**|**_mbsstr**|**wcsstr –**|
|**není k dispozici**|**není k dispozici**|**_mbsstr_l**|**není k dispozici**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strstr –**|\<String.h >|
|**wcsstr –**|\<String.h > nebo \<wchar.h >|
|**_mbsstr –**, **_mbsstr_l –**|\<Mbstring.h >|

Další informace o kompatibilitě najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string::Find](../../standard-library/basic-string-class.md#find)<br/>
