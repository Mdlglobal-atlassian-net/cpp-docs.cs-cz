---
title: vfscanf_s vfwscanf_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- vfscanf_s
- vfwscanf_s
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
- vfscanf_s
- vfwscanf_s
- _vftscanf_s
dev_langs:
- C++
ms.assetid: 9b0133f0-9a18-4581-b24b-3b72683ad432
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79b00ee0216120451c029b7de1caf9ac1967f802
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="vfscanfs-vfwscanfs"></a>vfscanf_s, vfwscanf_s

Čtení formátovaných dat z datového proudu. Tyto verze nástroje vfscanf vfwscanf mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int vfscanf_s(
   FILE *stream,
   const char *format,
   va_list arglist
);
int vfwscanf_s(
   FILE *stream,
   const wchar_t *format,
   va_list arglist
);

```

### <a name="parameters"></a>Parametry

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

*Formát*<br/>
Řetězec řízení formátu

*seznam_argumentů*<br/>
Seznam argumentů s proměnnou.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí počet polí, které jsou úspěšně převést a přiřadit; Návratová hodnota nezahrnuje pole, které byly pro čtení, ale není přiřazen. Vrácená hodnota 0 značí, že byly přiřazené žádné pole. Pokud dojde k chybě, nebo pokud je dosaženo konce datový proud souboru před prvním převodu, je vrácenou hodnotu **EOF** pro **vfscanf_s** a **vfwscanf_s**.

Tyto funkce ověřit jejich parametrů. Pokud *datového proudu* je ukazatel souboru je neplatný, nebo *formátu* je ukazatel s hodnotou null, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí **EOF** a nastavte **errno** k **einval –**.

## <a name="remarks"></a>Poznámky

**Vfscanf_s** funkce čte data z aktuální pozici *datového proudu* do umístění, která se poskytují *seznam_argumentů* seznam argumentů (pokud existuje). Každý argument v seznamu musí být ukazatel na proměnné typu, která odpovídá specifikátor typu v *formátu*. *Formát* ovládací prvky výklad vstupní pole a má stejnou tvoří a fungovat jako *formátu* argument pro **scanf_s –**; najdete v části [pole Specifikace formátu: Funkce scanf a wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md) popis *formátu*. **vfwscanf_s** je verze široká charakterová **vfscanf_s**; argument formátu **vfwscanf_s** je široká charakterová řetězec. Tyto funkce chovají stejně jako datový proud se při otevření v režimu ANSI. **vfscanf_s** vstup z datového proudu UNICODE aktuálně nepodporuje.

Hlavní rozdíl mezi bezpečnější funkce (které mají **_Malá** příponu) a jiné verze je, že bezpečnější funkce vyžadovat velikosti ve znacích jednotlivých **c**, **C**, **s**, **S**, a **[** typ pole, které chcete předat jako argument okamžitě následující proměnné. Další informace najdete v tématu [scanf_s –, _scanf_s_l –, wscanf_s –, _wscanf_s_l –](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) a [specifikace šířky scanf](../../c-runtime-library/scanf-width-specification.md).

> [!NOTE]
> Parametr velikosti je typu **nepodepsané**, nikoli **size_t –**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftscanf_s**|**vfscanf_s**|**vfscanf_s**|**vfwscanf_s**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**vfscanf_s**|\<stdio.h>|
|**vfwscanf_s**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_vfscanf_s.c
// compile with: /W3
// This program writes formatted
// data to a file. It then uses vfscanf_s to
// read the various data back from the file.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

FILE *stream;

int call_vfscanf_s(FILE * istream, char * format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vfscanf_s(istream, format, arglist);
    va_end(arglist);
    return result;
}

int main(void)
{
    long l;
    float fp;
    char s[81];
    char c;

    if (fopen_s(&stream, "vfscanf_s.out", "w+") != 0)
    {
        printf("The file vfscanf_s.out was not opened\n");
    }
    else
    {
        fprintf(stream, "%s %ld %f%c", "a-string",
            65000, 3.14159, 'x');
        // Security caution!
        // Beware loading data from a file without confirming its size,
        // as it may lead to a buffer overrun situation.

        // Set pointer to beginning of file:
        fseek(stream, 0L, SEEK_SET);

        // Read data back from file:
        call_vfscanf_s(stream, "%s %ld %f%c", s, _countof(s), &l, &fp, &c, 1);

        // Output data read:
        printf("%s\n", s);
        printf("%ld\n", l);
        printf("%f\n", fp);
        printf("%c\n", c);

        fclose(stream);
    }
}

```

```Output
a-string
65000
3.141590
x
```

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)<br/>
[fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[vfscanf, vfwscanf](vfscanf-vfwscanf.md)<br/>
