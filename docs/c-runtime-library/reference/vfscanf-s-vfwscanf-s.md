---
title: vfscanf_s, vfwscanf_s
ms.date: 11/04/2016
api_name:
- vfscanf_s
- vfwscanf_s
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
- vfscanf_s
- vfwscanf_s
- _vftscanf_s
ms.assetid: 9b0133f0-9a18-4581-b24b-3b72683ad432
ms.openlocfilehash: 2c6f3504c9c12ad5429a1b9649eda351c473671a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957379"
---
# <a name="vfscanf_s-vfwscanf_s"></a>vfscanf_s, vfwscanf_s

Čte formátovaná data z datového proudu. Tyto verze vfscanf, vfwscanf mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*stream*<br/>
Ukazatel na strukturu **souborů** .

*format*<br/>
Řetězec řízení formátu

*arglist*<br/>
Seznam argumentů proměnných

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí počet polí, která jsou úspěšně převedena a přiřazena; Vrácená hodnota nezahrnuje pole, která byla načtena, ale nebyla přiřazena. Návratová hodnota 0 značí, že nebyla přiřazena žádná pole. Pokud dojde k chybě nebo pokud je před prvním převodem dosaženo konce souboru datového proudu, je vrácená hodnota znak **EOF** pro **vfscanf_s** a **vfwscanf_s**.

Tyto funkce ověřují své parametry. Pokud je *datový proud* neplatný ukazatel na *soubor nebo je* nastaven ukazatel s hodnotou null, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EOF** a nastaví **errno** na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **vfscanf_s** čte data z aktuální pozice *datového proudu* do umístění, která jsou uvedena v seznamu argumentů *Arglist* (pokud existuje). Každý argument v seznamu musí být ukazatel na proměnnou typu, který odpovídá specifikátoru typu ve *formátu*. *Formát* řídí interpretaci vstupních polí a má stejnou formu a funkci jako argument *Format* pro **scanf_s**; Popis *formátu*naleznete v části [pole specifikace formátu: scanf a wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md) . **vfwscanf_s** je **vfscanf_s**verze s velkým znakem; argument Format pro **vfwscanf_s** je řetězec s velkým znakem. Tyto funkce se chovají stejně, pokud je datový proud otevřen v režimu ANSI. **vfscanf_s** v současné době nepodporuje vstup z datového proudu Unicode.

Hlavním rozdílem mezi bezpečnějšími funkcemi (které mají příponu **_s** ) a ostatními verzemi je, že bezpečnější funkce vyžadují velikost ve znacích každého pole **c**, **c**, **s**, a **[** **Type, které**má být předán jako argument bezprostředně za proměnnou. Další informace najdete v tématu [specifikace šířky](../../c-runtime-library/scanf-width-specification.md) [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) a scanf.

> [!NOTE]
> Parametr size je typu **bez znaménka**, nikoli **size_t**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftscanf_s**|**vfscanf_s**|**vfscanf_s**|**vfwscanf_s**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**vfscanf_s**|\<stdio.h>|
|**vfwscanf_s**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)<br/>
[fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[vfscanf, vfwscanf](vfscanf-vfwscanf.md)<br/>
