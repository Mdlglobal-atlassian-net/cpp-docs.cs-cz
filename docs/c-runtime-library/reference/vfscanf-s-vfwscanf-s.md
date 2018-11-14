---
title: vfscanf_s, vfwscanf_s
ms.date: 11/04/2016
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
ms.assetid: 9b0133f0-9a18-4581-b24b-3b72683ad432
ms.openlocfilehash: 7f2f39ef124220ddee0b42242a9991d63fe5969a
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521243"
---
# <a name="vfscanfs-vfwscanfs"></a>vfscanf_s, vfwscanf_s

Čtení formátovaných dat z datového proudu. Tyto verze vfscanf, vfwscanf mají rozšíření zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Stream*<br/>
Ukazatel na **souboru** struktury.

*Formát*<br/>
Řetězec řízení formátu

*seznam_argumentů*<br/>
Seznam argumentů s proměnnou délkou.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí počet polí, která jsou úspěšně převedena a přidělena; Vrácená hodnota nezahrnuje pole, která byla načtena, ale nejsou přiřazena. Vrácená hodnota 0 označuje, že nebyla přiřazena žádná pole. Pokud dojde k chybě nebo pokud je dosaženo konce souboru datového proudu před prvním převodem, vrácená hodnota je **EOF** pro **vfscanf_s** a **vfwscanf_s**.

Tyto funkce ověřují své parametry. Pokud *stream* je neplatný ukazatel na soubor, nebo *formátu* je ukazatel s hodnotou null, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EOF** a nastavte **errno** k **EINVAL**.

## <a name="remarks"></a>Poznámky

**Vfscanf_s** funkce čte data z aktuální pozice *stream* do umístění, která jsou uvedena v každém *seznam_argumentů* seznam argumentů (pokud existuje). Každý argument v seznamu musí být ukazatel na proměnnou typu, který odpovídá specifikátoru typů ve *formátu*. *Formát* řídí interpretaci vstupních polí a má stejnou formu a funkci, jako *formátu* argument pro **scanf_s**; naleznete v tématu [pole Specifikace formátu: Funkce scanf a wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md) popis *formátu*. **vfwscanf_s** je verze širokého znaku **vfscanf_s**; argument formátu **vfwscanf_s** je širokoznaký řetězec. Tyto funkce chovají stejně jako v případě, že datový proud je otevřen v režimu ANSI. **vfscanf_s** aktuálně nepodporuje vstup z datového proudu UNICODE.

Hlavní rozdíl mezi bezpečnějšími funkcemi (které mají **_Malá** přípona) a ostatními verzemi je, že bezpečnější funkce vyžadují velikost znaků jednotlivých **c**, **C**, **s**, **S**, a **[** typu pole být předán jako argument bezprostředně následující proměnnou. Další informace najdete v tématu [scanf_s _scanf_s_l –, wscanf_s – _wscanf_s_l –](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) a [specifikace šířky scanf](../../c-runtime-library/scanf-width-specification.md).

> [!NOTE]
> Velikost parametru je typu **bez znaménka**, nikoli **size_t**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftscanf_s**|**vfscanf_s**|**vfscanf_s**|**vfwscanf_s**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**vfscanf_s**|\<stdio.h>|
|**vfwscanf_s**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)<br/>
[fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[vfscanf, vfwscanf](vfscanf-vfwscanf.md)<br/>
