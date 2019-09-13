---
title: vsscanf_s, vswscanf_s
ms.date: 11/04/2016
api_name:
- vswscanf_s
- vsscanf_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- vsscanf_s
- vswscanf_s
- _vstscanf_s
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
ms.openlocfilehash: bacda4288a6745ea57c31e68e515ae7b37418096
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946021"
---
# <a name="vsscanf_s-vswscanf_s"></a>vsscanf_s, vswscanf_s

Přečte formátovaná data z řetězce. Tyto verze [vsscanf, vswscanf](vsscanf-vswscanf.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int vsscanf_s(
   const char *buffer,
   const char *format,
   va_list argptr
);
int vswscanf_s(
   const wchar_t *buffer,
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>Parametry

*vyrovnávací paměti*<br/>
Uložená data

*format*<br/>
Řetězec řízení formátu Další informace najdete v tématu [formátování pole Specifikace: scanf a wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*arglist*<br/>
Seznam argumentů proměnných

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí počet polí, která jsou úspěšně převedena a přiřazena; Vrácená hodnota nezahrnuje pole, která byla načtena, ale nebyla přiřazena. Návratová hodnota 0 značí, že nebyla přiřazena žádná pole. Návratová hodnota je znak **EOF** pro chybu, nebo pokud je dosaženo konce řetězce před prvním převodem.

Pokud je *vyrovnávací paměť* nebo *Formát* ukazatel s **hodnotou null** , je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce hodnotu-1 a nastaví **errno** na **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **vsscanf_s** čte data z *vyrovnávací paměti* do umístění, která jsou uvedena v každém argumentu v seznamu argumentů *Arglist* . Argumenty v seznamu argumentů určují ukazatele na proměnné, které mají typ odpovídající specifikátoru typu ve *formátu*. Na rozdíl od méně bezpečné verze **vsscanf**je vyžadován parametr velikosti vyrovnávací paměti, pokud použijete znaky pole Type **c**, **c**, **s**, **s**nebo sady řízení řetězce, které jsou uzavřeny v **[]** . Velikost vyrovnávací paměti ve znacích se musí zadat jako další parametr hned za parametrem vyrovnávací paměti, který to vyžaduje.

Velikost vyrovnávací paměti zahrnuje ukončující hodnotu null. Pole Specifikace šířky se dá použít k zajištění toho, že token, který je čten v, se vejde do vyrovnávací paměti. Pokud není použito pole Specifikace šířky a token načtený v je příliš velký, aby se vešel do vyrovnávací paměti, do této vyrovnávací paměti se nezapisuje žádné informace.

Další informace naleznete v tématu [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) a [scanf Type Characters Field](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Parametr size je typu **bez znaménka**, nikoli **size_t**.

Argument *Format* řídí interpretaci vstupních polí a má stejnou formu a funkci jako argument *Format* pro funkci **scanf_s** . Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

**vswscanf_s** je **vsscanf_s**verze s velkým znakem; argumenty **vswscanf_s** jsou řetězce s libovolným znakem. **vsscanf_s** nezpracovává vícebajtové šestnáctkové znaky. **vswscanf_s** nezpracovává šestnáctkové znaky Unicode s plnou šířkou nebo "zónu kompatibility". V opačném případě se **vswscanf_s** a **vsscanf_s** chovají stejně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstscanf_s**|**vsscanf_s**|**vsscanf_s**|**vswscanf_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**vsscanf_s**|\<stdio.h>|
|**vswscanf_s**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_vsscanf_s.c
// compile with: /W3
// This program uses vsscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

int call_vsscanf_s(char *tokenstring, char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vsscanf_s(tokenstring, format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    char  tokenstring[] = "15 12 14...";
    char  s[81];
    char  c;
    int   i;
    float fp;

    // Input various data from tokenstring:
    // max 80 character string:
    call_vsscanf_s(tokenstring, "%80s", s, _countof(s));
    call_vsscanf_s(tokenstring, "%c", &c, sizeof(char));
    call_vsscanf_s(tokenstring, "%d", &i);
    call_vsscanf_s(tokenstring, "%f", &fp);

    // Output the data read
    printf("String    = %s\n", s);
    printf("Character = %c\n", c);
    printf("Integer:  = %d\n", i);
    printf("Real:     = %f\n", fp);
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vsscanf, vswscanf](vsscanf-vswscanf.md)<br/>
