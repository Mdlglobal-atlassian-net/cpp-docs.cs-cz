---
title: strcpy – wcscpy –, _mbscpy – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- strcpy
- wcscpy
- _mbscpy
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
- _mbscpy
- _ftcscpy
- wcscpy
- _tcscpy
- strcpy
dev_langs:
- C++
helpviewer_keywords:
- strcpy function
- tcscpy function
- ftcscpy function
- mbscpy function
- wcscpy function
- copying strings
- strings [C++], copying
- _tcscpy function
- _ftcscpy function
- _mbscpy function
ms.assetid: f97a4f81-e9ee-4f15-888a-0fa5d7094c5a
caps.latest.revision: 31
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 761cb15f0045741b8397c559600f6a21b150fa4d
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="strcpy-wcscpy-mbscpy"></a>strcpy, wcscpy, _mbscpy

Zkopíruje řetězec. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [strcpy_s – wcscpy_s –, _mbscpy_s –](strcpy-s-wcscpy-s-mbscpy-s.md).

> [!IMPORTANT]
> **_mbscpy –** nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *strcpy(
   char *strDestination,
   const char *strSource
);
wchar_t *wcscpy(
   wchar_t *strDestination,
   const wchar_t *strSource
);
unsigned char *_mbscpy(
   unsigned char *strDestination,
   const unsigned char *strSource
);
template <size_t size>
char *strcpy(
   char (&strDestination)[size],
   const char *strSource
); // C++ only
template <size_t size>
wchar_t *wcscpy(
   wchar_t (&strDestination)[size],
   const wchar_t *strSource
); // C++ only
template <size_t size>
unsigned char *_mbscpy(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource
); // C++ only
```

### <a name="parameters"></a>Parametry

*strDestination*<br/>
Cílový řetězec.

*strSource*<br/>
Řetězce ukončené hodnotou Null zdroje.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí cílový řetězec. Žádnou návratovou hodnotu je vyhrazena indikující chybu.

## <a name="remarks"></a>Poznámky

**Strcpy –** funkce kopie *strSource*, včetně ukončující znak hodnoty null do umístění, která je zadána *strDestination*. Chování **strcpy –** není definován, pokud se překrývají zdrojové a cílové řetězce.

> [!IMPORTANT]
> Protože **strcpy –** nekontroluje dostatek místa v *strDestination* před kopíruje *strSource*, je potenciální příčinou přetečení vyrovnávací paměti. Proto doporučujeme použít [strcpy_s –](strcpy-s-wcscpy-s-mbscpy-s.md) místo.

**wcscpy –** a **_mbscpy –** , jsou široká charakterová a vícebajtových znaků verze **strcpy –**. Argumenty a vrací hodnotu **wcscpy –** jsou široká charakterová řetězce; u **_mbscpy –** jsou řetězců vícebajtových znaků. Tyto tři funkce chovají stejně jako jinak.

V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscpy –**|**strcpy**|**_mbscpy**|**wcscpy**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strcpy**|\<String.h >|
|**wcscpy**|\<String.h > nebo \<wchar.h >|
|**_mbscpy**|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strcpy.c
// compile with: /W3
// This program uses strcpy
// and strcat to build a phrase.

#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[80];

   // If you change the previous line to
   //   char string[20];
   // strcpy and strcat will happily overrun the string
   // buffer.  See the examples for strncpy and strncat
   // for safer string handling.

   strcpy( string, "Hello world from " ); // C4996
   // Note: strcpy is deprecated; use strcpy_s instead
   strcat( string, "strcpy " );           // C4996
   // Note: strcat is deprecated; use strcat_s instead
   strcat( string, "and " );              // C4996
   strcat( string, "strcat!" );           // C4996
   printf( "String = %s\n", string );
}
```

```Output
String = Hello world from strcpy and strcat!
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
