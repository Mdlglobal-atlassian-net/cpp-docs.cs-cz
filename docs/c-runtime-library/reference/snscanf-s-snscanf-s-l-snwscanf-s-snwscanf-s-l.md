---
title: _snscanf_s –, _snscanf_s_l –, _snwscanf_s –, _snwscanf_s_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _snwscanf_s_l
- _snwscanf_s
- _snscanf_s
- _snscanf_s_l
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
apitype: DLLExport
f1_keywords:
- _sntscanf_s
- snscanf_s
- _snwscanf_s_l
- sntscanf_s_l
- snwscanf_s_l
- snwscanf_s
- _snscanf_s
- _snwscanf_s
- snscanf_s_l
- _sntscanf_s_l
- _snscanf_s_l
- sntscanf_s
dev_langs:
- C++
helpviewer_keywords:
- _snscanf_s_l function
- snwscanf_s function
- _snwscanf_s function
- sntscanf_s_l function
- sntscanf_s function
- _snwscanf_s_l function
- _snscanf_s function
- snscanf_s_l function
- strings [C++], reading data from
- _sntscanf_s_l function
- reading data, strings
- snscanf_s function
- strings [C++], reading
- _sntscanf_s function
- snwscanf_s_l function
ms.assetid: 72356653-7362-461a-af73-597b9c0a8094
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0253b8c103d3125810aab48606d7a20099827e6f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="snscanfs-snscanfsl-snwscanfs-snwscanfsl"></a>_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l

Čtení formátovaných dat o zadané délce z řetězce. Toto jsou verze [_snscanf –, _snscanf_l –, _snwscanf –, _snwscanf_l –](snscanf-snscanf-l-snwscanf-snwscanf-l.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int __cdecl _snscanf_s(
   const char * input,
   size_t length,
   const char * format [, argument_list]
);
int __cdecl _snscanf_s_l(
   const char * input,
   size_t length,
   const char * format,
   locale_t locale [, argument_list]
);
int __cdecl _snwscanf_s(
   const wchar_t * input,
   size_t length,
   const wchar_t * format [, argument_list]
);
int __cdecl _snwscanf_s_l(
   const wchar_t * input,
   size_t length,
   const wchar_t * format,
   locale_t locale [, argument_list]
);
```

### <a name="parameters"></a>Parametry

*Vstup*<br/>
Vstupní řetězec prozkoumat.

*Délka*<br/>
Počet znaků k prozkoumání v *vstupní*.

*Formát*<br/>
Specifikátory formátu jeden nebo více.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

*argument_list*<br/>
Nepovinné argumenty pro přiřazení podle řetězec formátu.

## <a name="return-value"></a>Návratová hodnota

Obě tyto funkce vrátí počet polí úspěšně převést a přiřazení; Návratová hodnota nezahrnuje pole, které byly pro čtení, ale není přiřazen. Vrácená hodnota 0 značí, že byly přiřazené žádné pole. Vrácená hodnota je **EOF** pro chybu nebo pokud je dosaženo konce řetězec před první převod. Další informace najdete v tématu [sscanf_s –, _sscanf_s_l –, swscanf_s –, _swscanf_s_l –](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).

Pokud *vstupní* nebo *formátu* je **NULL** ukazatele, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí **EOF** a nastavte **errno** k **einval –**.

Informace o těchto a dalších kódy chyb naleznete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Tato funkce je stejná jako **sscanf_s –** s tím rozdílem, že poskytuje možnost určit pevný počet znaků k prozkoumání ze vstupního řetězce. Další informace najdete v tématu [sscanf_s –, _sscanf_s_l –, swscanf_s –, _swscanf_s_l –](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).

Parametr velikosti vyrovnávací paměti je požadován spolu s znaky pole typu **c**, **C**, **s**, **S**, a **[** . Další informace najdete v tématu [znaky pole typu scanf](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Parametr velikosti je typu **nepodepsané**, nikoli **size_t –**.

Verze tyto funkce s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntscanf_s –**|**_snscanf_s**|**_snscanf_s**|**_snwscanf_s**|
|**_sntscanf_s_l –**|**_snscanf_s_l**|**_snscanf_s_l**|**_snwscanf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_snscanf_s –**, **_snscanf_s_l –**|\<stdio.h>|
|**_snwscanf_s –**, **_snwscanf_s_l –**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_snscanf_s.c
// This example scans a string of
// numbers, using both the character
// and wide character secure versions
// of the snscanf function.

#include <stdio.h>

int main( )
{
    char        str1[] = "15 12 14...";
    wchar_t     str2[] = L"15 12 14...";
    char        s1[3];
    wchar_t     s2[3];
    int         i;
    float       fp;

    i = _snscanf_s( str1, 6,  "%s %f", s1, 3, &fp);
    printf_s("_snscanf_s converted %d fields: ", i);
    printf_s("%s and %f\n", s1, fp);

    i = _snwscanf_s( str2, 6,  L"%s %f", s2, 3, &fp);
    wprintf_s(L"_snwscanf_s converted %d fields: ", i);
    wprintf_s(L"%s and %f\n", s2, fp);
}
```

```Output
_snscanf_s converted 2 fields: 15 and 12.000000
_snwscanf_s converted 2 fields: 15 and 12.000000
```

## <a name="see-also"></a>Viz také

[scanf – specifikace šířky](../../c-runtime-library/scanf-width-specification.md)<br/>
