---
title: vscanf_s, vwscanf_s
ms.date: 11/04/2016
api_name:
- vscanf_s
- vwscanf_s
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
- _vtscanf_s
- vscanf_s
- vwscanf_s
ms.assetid: 23a1c383-5b01-4887-93ce-534a1e38ed93
ms.openlocfilehash: 4d08679d08fb5b212306cbaeec200d16803a85ef
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945401"
---
# <a name="vscanf_s-vwscanf_s"></a>vscanf_s, vwscanf_s

Přečte formátovaná data ze standardního vstupního datového proudu. Tyto verze [vscanf, vwscanf](vscanf-vwscanf.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int vscanf_s(
   const char *format,
   va_list arglist
);
int vwscanf_s(
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>Parametry

*format*<br/>
Formátovací řetězec ovládacího prvku

*arglist*<br/>
Seznam argumentů proměnných

## <a name="return-value"></a>Návratová hodnota

Vrátí počet úspěšně převedených a přiřazených polí. Vrácená hodnota nezahrnuje pole, která byla načtena, ale nebyla přiřazena. Návratová hodnota 0 značí, že nebyla přiřazena žádná pole. Vrácená hodnota je **EOF** pro chybu, nebo pokud se při prvním pokusu o čtení znaku objevil znak konce souboru nebo znak konce řetězce. Pokud je *Format* ukazatel s **hodnotou null** , je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **vscanf_s** a **vwscanf_s** vrátí **EOF** a nastaví **errno** na **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **vscanf_s** čte data ze standardního vstupního streamu **stdin** a zapisuje data do umístění, která jsou uvedena v seznamu argumentů *Arglist* . Každý argument v seznamu musí být ukazatel na proměnnou typu, který odpovídá specifikátoru typu ve *formátu*. Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

**vwscanf_s** je **vscanf_s**verze s velkým znakem; Argument *Format* pro **vwscanf_s** je řetězec s velkým znakem. **vwscanf_s** a **vscanf_s** se chovají stejně, pokud je datový proud otevřen v režimu ANSI. **vscanf_s** nepodporuje vstup z datového proudu Unicode.

Na rozdíl od **vscanf** a **vwscanf**vyžadují **vscanf_s** a **vwscanf_s** velikost vyrovnávací paměti pro všechny vstupní parametry typu **c**, **c**, **s**nebo sady řízení řetězce,které jsou uzavřeny v **[].** . Velikost vyrovnávací paměti ve znacích je předána jako další parametr bezprostředně po ukazateli na vyrovnávací paměť nebo proměnnou. Velikost vyrovnávací paměti ve znacích pro řetězec **wchar_t** není stejná jako velikost v bajtech.

Velikost vyrovnávací paměti zahrnuje ukončující hodnotu null. Pole s určením šířky můžete použít k zajištění, že token, který je čten v, se vejde do vyrovnávací paměti. Pokud není použito pole Specifikace šířky a token načtený v je příliš velký, aby se vešel do vyrovnávací paměti, do této vyrovnávací paměti se nezapisuje žádné informace.

> [!NOTE]
> Parametr *Size* je typu **bez znaménka**, nikoli **size_t**.

Další informace najdete v tématu [specifikace šířky scanf](../../c-runtime-library/scanf-width-specification.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtscanf_s**|**vscanf_s**|**vscanf_s**|**vwscanf_s**|

Další informace najdete v tématu [formátování pole Specifikace: scanf a wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**vscanf_s**|\<stdio.h>|
|**wscanf_s**|\<stdio. h > nebo \<WCHAR. h >|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou, **stdin**, **stdout**a **stderr**, musí být přesměrované před tím, než je funkce modulu runtime jazyka C můžou použít v aplikacích pro UWP. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_vscanf_s.c
// compile with: /W3
// This program uses the vscanf_s and vwscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

int call_vscanf_s(char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vscanf_s(format, arglist);
    va_end(arglist);
    return result;
}

int call_vwscanf_s(wchar_t *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vwscanf_s(format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    int   i, result;
    float fp;
    char  c, s[81];
    wchar_t wc, ws[81];
    result = call_vscanf_s("%d %f %c %C %s %S", &i, &fp, &c, 1,
                           &wc, 1, s, _countof(s), ws, _countof(ws) );
    printf( "The number of fields input is %d\n", result );
    printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);
    result = call_vwscanf_s(L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                            &wc, 1, s, _countof(s), ws, _countof(ws) );
    wprintf( L"The number of fields input is %d\n", result );
    wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);
}
```

Když se tomuto programu udělí vstup v příkladu, vytvoří tento výstup:

```Input
71 98.6 h z Byte characters
36 92.3 y n Wide characters
```

```Output
The number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[vscanf, vwscanf](vscanf-vwscanf.md)<br/>
