---
title: vfscanf, vfwscanf
ms.date: 11/04/2016
api_name:
- vfwscanf
- vfscanf
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
- vfwscanf
- _vftscanf
- vfscanf
ms.assetid: c06450ef-03f1-4d24-a8ac-d2dd98847918
ms.openlocfilehash: 72591c9fa91855745f45f3f77c88dd0ed5b001a0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945524"
---
# <a name="vfscanf-vfwscanf"></a>vfscanf, vfwscanf

Čte formátovaná data z datového proudu. K dispozici jsou bezpečnější verze těchto funkcí; viz [vfscanf_s, vfwscanf_s](vfscanf-s-vfwscanf-s.md).

## <a name="syntax"></a>Syntaxe

```C
int vfscanf(
   FILE *stream,
   const char *format,
   va_list argptr
);
int vfwscanf(
   FILE *stream,
   const wchar_t *format,
   va_list argptr
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

Každá z těchto funkcí vrátí počet polí, která jsou úspěšně převedena a přiřazena; Vrácená hodnota nezahrnuje pole, která jsou čtena, ale nejsou přiřazena. Návratová hodnota 0 značí, že nebyla přiřazena žádná pole. Pokud dojde k chybě nebo pokud je před prvním převodem dosaženo konce souboru datového proudu, je vrácená hodnota znak **EOF** pro **vfscanf** a **vfwscanf**.

Tyto funkce ověřují své parametry. Pokud je *datový proud* nebo *Formát* ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EOF** a nastaví **errno** na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **vfscanf** čte data z aktuální pozice *datového proudu* do umístění, která jsou uvedena v seznamu argumentů *Arglist* . Každý argument v seznamu musí být ukazatel na proměnnou typu, který odpovídá specifikátoru typu ve *formátu*. *Formát* řídí interpretaci vstupních polí a má stejnou formu a funkci jako argument *Format* pro **scanf**; Popis *formátu*naleznete v tématu [scanf](scanf-scanf-l-wscanf-wscanf-l.md) .

**vfwscanf** je **vfscanf**verze s velkým znakem; argument Format pro **vfwscanf** je řetězec s velkým znakem. Tyto funkce se chovají stejně, pokud je datový proud otevřen v režimu ANSI. **vfscanf** nepodporuje vstup z datového proudu Unicode.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftscanf**|**vfscanf**|**vfscanf**|**vfwscanf**|

Další informace najdete v tématu [formátování pole Specifikace: scanf a wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**vfscanf**|\<stdio.h>|
|**vfwscanf**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_vfscanf.c
// compile with: /W3
// This program writes formatted
// data to a file. It then uses vfscanf to
// read the various data back from the file.

#include <stdio.h>
#include <stdarg.h>

FILE *stream;

int call_vfscanf(FILE * istream, char * format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vfscanf(istream, format, arglist);
    va_end(arglist);
    return result;
}

int main(void)
{
    long l;
    float fp;
    char s[81];
    char c;

    if (fopen_s(&stream, "vfscanf.out", "w+") != 0)
    {
        printf("The file vfscanf.out was not opened\n");
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
        call_vfscanf(stream, "%s %ld %f%c", s, &l, &fp, &c);

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
[_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
[vfscanf_s, vfwscanf_s](vfscanf-s-vfwscanf-s.md)<br/>
