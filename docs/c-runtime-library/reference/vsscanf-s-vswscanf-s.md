---
title: vsscanf_s vswscanf_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- vswscanf_s
- vsscanf_s
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
- vsscanf_s
- vswscanf_s
- _vstscanf_s
dev_langs:
- C++
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbcf6d0a8b54cc08242d613b24c415ac1ef05fd3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="vsscanfs-vswscanfs"></a>vsscanf_s, vswscanf_s

Čtení formátovaných dat z řetězce. Tyto verze nástroje [vsscanf –, vswscanf –](vsscanf-vswscanf.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Vyrovnávací paměti*<br/>
Uložená data

*Formát*<br/>
Řetězec řízení formátu Další informace najdete v tématu [pole Specifikace formátu: funkce scanf a wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*seznam_argumentů*<br/>
Seznam argumentů s proměnnou.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí počet polí, které jsou úspěšně převést a přiřadit; Návratová hodnota nezahrnuje pole, které byly pro čtení, ale není přiřazen. Vrácená hodnota 0 značí, že byly přiřazené žádné pole. Vrácená hodnota je **EOF** pro chybu nebo pokud je dosaženo konce řetězec před první převod.

Pokud *vyrovnávací paměti* nebo *formátu* je **NULL** ukazatele, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte **errno** k **einval –**.

Informace o těchto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**Vsscanf_s** funkce Číst data z *vyrovnávací paměti* do umístění, které jsou uvedeny v každém argumentu ve *seznam_argumentů* seznam argumentů. Zadejte argumenty v seznamu argumentů ukazatele na proměnné, které mají typ, který odpovídá specifikátor typu v *formátu*. Na rozdíl od méně bezpečná verze **vsscanf –**, parametr velikost vyrovnávací paměti je povinný při použití znaky pole typu **c**, **C**, **s**, **S**, nebo nastaví řetězec řízení, které se nacházejí v **[]**. Velikost vyrovnávací paměti ve znacích je nutné zadat jako dodatečný parametr ihned po každé parametr vyrovnávací paměti, který vyžaduje.

Velikost vyrovnávací paměti zahrnuje ukončující hodnotu null. Pole Specifikace šířky lze zajistit, že token, který je pro čtení v se vejde do vyrovnávací paměti. Pokud se používá žádné pole Specifikace šířky a token, přečtěte si je příliš velký, aby se vešla do vyrovnávací paměti, nic se zapíše do této vyrovnávací paměti.

Další informace najdete v tématu [scanf_s –, _scanf_s_l –, wscanf_s –, _wscanf_s_l –](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) a [znaky pole typu scanf](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Parametr velikosti je typu **nepodepsané**, nikoli **size_t –**.

*Formátu* ovládací prvky argument výklad vstupní pole a má stejnou tvoří a fungovat jako *formátu* argument **scanf_s –** funkce. Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

**vswscanf_s** je verze široká charakterová **vsscanf_s**; argumenty, které mají **vswscanf_s** jsou široká charakterová řetězce. **vsscanf_s** nezpracovává vícebajtové hexadecimálních znaků. **vswscanf_s** nezpracovává šestnáctkové kódování Unicode s plnou šířkou nebo znaků "kompatibility zóna". V opačném **vswscanf_s** a **vsscanf_s** chovají stejně jako.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstscanf_s**|**vsscanf_s**|**vsscanf_s**|**vswscanf_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**vsscanf_s**|\<stdio.h>|
|**vswscanf_s**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vsscanf, vswscanf](vsscanf-vswscanf.md)<br/>
