---
title: _snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l
ms.date: 11/04/2016
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
- ntoskrnl.exe
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
ms.openlocfilehash: 8d56999aea69c4674070410774d5a2fa11abb178
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210546"
---
# <a name="snscanfs-snscanfsl-snwscanfs-snwscanfsl"></a>_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l

Čtení formátovaných dat z řetězce zadané délky. Jde o verzích [_snscanf – _snscanf_l –, _snwscanf – _snwscanf_l –](snscanf-snscanf-l-snwscanf-snwscanf-l.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Jeden nebo více specifikátorů formátu.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

*argument_list*<br/>
Volitelné argumenty pro přiřazení podle formátovací řetězec.

## <a name="return-value"></a>Návratová hodnota

Obě tyto funkce vrátí počet polí úspěšně převedena a přidělena; Vrácená hodnota nezahrnuje pole, která byla načtena, ale nejsou přiřazena. Vrácená hodnota 0 označuje, že nebyla přiřazena žádná pole. Vrácená hodnota je **EOF** pro chybu nebo pokud je dosaženo konce řetězce před prvním převodem. Další informace najdete v tématu [sscanf_s – _sscanf_s_l –, swscanf_s – _swscanf_s_l –](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).

Pokud *vstupní* nebo *formátu* je **NULL** vyvolána ukazatel, obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EOF** a nastavte **errno** k **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Tato funkce je třeba **sscanf_s –** s tím rozdílem, že poskytuje možnost určit pevný počet znaků k prozkoumání ze vstupního řetězce. Další informace najdete v tématu [sscanf_s – _sscanf_s_l –, swscanf_s – _swscanf_s_l –](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).

Parametr velikosti vyrovnávací paměti je požadován spolu s znaky pole typu **c**, **C**, **s**, **S**, a **[** . Další informace najdete v tématu [scanf – znaky pole typu](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Velikost parametru je typu **bez znaménka**, nikoli **size_t**.

Verze těchto funkcí s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí předaného namísto aktuálního národní prostředí pro vlákno.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntscanf_s**|**_snscanf_s**|**_snscanf_s**|**_snwscanf_s**|
|**_sntscanf_s_l**|**_snscanf_s_l**|**_snscanf_s_l**|**_snwscanf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_snscanf_s**, **_snscanf_s_l**|\<stdio.h>|
|**_snwscanf_s**, **_snwscanf_s_l**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[scanf – specifikace šířky](../../c-runtime-library/scanf-width-specification.md)<br/>
