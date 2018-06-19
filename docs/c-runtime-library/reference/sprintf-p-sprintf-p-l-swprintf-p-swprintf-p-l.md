---
title: _sprintf_p –, _sprintf_p_l –, _swprintf_p –, _swprintf_p_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _sprintf_p
- _swprintf_p_l
- _swprintf_p
- _sprintf_p_l
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
- _sprintf_p
- _swprintf_p_l
- _sprintf_p_l
- _swprintf_p
- sprintf_p
- swprint_p_l
- swprintf_p
- swprintf_p_l
dev_langs:
- C++
helpviewer_keywords:
- sprintf_p_l function
- swprintf_p function
- swprintf_p_l function
- _sprintf_p function
- _sprintf_p_l function
- _swprintf_p function
- sprintf_p function
- _stprintf_p function
- stprintf_p function
- _swprintf_p_l function
- stprintf_p_l function
- formatted text [C++]
- _stprintf_p_l function
ms.assetid: a2ae78e8-6b0c-48d5-87a9-ea2365b0693d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02c28da8c066f51bb4366c7ed20e04266d37b074
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451409"
---
# <a name="sprintfp-sprintfpl-swprintfp-swprintfpl"></a>_sprintf_p –, _sprintf_p_l –, _swprintf_p –, _swprintf_p_l –

Umožňuje určit pořadí, že parametry jsou použity v řetězec formátu zápisu formátovaná data na řetězec.

## <a name="syntax"></a>Syntaxe

```C
int _sprintf_p(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format [,
   argument_list]
);
int _sprintf_p_l(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   locale_t locale [,
   argument_list]
);
int _swprintf_p(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format [,
   argument_list]
);
int _swprintf_p_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   locale_t locale [,
   argument_list]
);
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Umístění úložiště pro výstup

*sizeOfBuffer*<br/>
Maximální počet znaků, které se mají uložit

*Formát*<br/>
Řetězec řízení formátu

*argument_list*<br/>
Nepovinné argumenty řetězce formátu.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Návratová hodnota

Počet znaků, které jsou zapsány nebo -1, pokud došlo k chybě.

## <a name="remarks"></a>Poznámky

**_Sprintf_p –** funkce naformátuje a ukládá řady znaků a hodnot v *vyrovnávací paměti*. Každý argument *argument_list* (pokud existuje) je převeden a výstup podle odpovídající specifikaci formátu v *formátu*. *Formátu* používá argument [formátu syntaxe specifikace pro funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md). Znak hodnoty null se připojí po poslední znak zapsána. Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno. Rozdíl mezi **_sprintf_p –** a **sprintf_s –** je, že **_sprintf_p –** podporuje poziční parametry, které umožní určení pořadí, ve kterém jsou argumenty použít ve formátovacím řetězci. Další informace najdete v tématu [printf_p – poziční parametry](../../c-runtime-library/printf-p-positional-parameters.md).

**_swprintf_p –** je verze široká charakterová **_sprintf_p –**; ukazatel argumenty, které mají **_swprintf_p –** jsou široká charakterová řetězce. Detekce chyb v kódování **_swprintf_p –** se můžou lišit od v **_sprintf_p –**. **_swprintf_p –** a **fwprintf_p –** vyjma toho, že se chovají stejně jako **_swprintf_p –** zapíše výstup na řetězec, spíše než do cílového umístění v typu **souboru**, a **_swprintf_p –** vyžaduje *počet* parametru určete maximální počet znaků, který má být zapsána. Verze tyto funkce s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.

**_sprintf_p –** vrátí počet bajtů, které jsou uložené v *vyrovnávací paměti*, není počítání ukončující znak hodnoty null. **_swprintf_p –** vrátí počet široké znaky, které jsou uložené v *vyrovnávací paměti*, není počítání ukončující široká znaková hodnotu null. Pokud *vyrovnávací paměti* nebo *formátu* je ukazatel s hodnotou null, nebo pokud řetězec formátu obsahuje neplatné znaky formátování, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru ](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte **errno** k **einval –**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_p –**|**_sprintf_p**|**_sprintf_p**|**_swprintf_p**|
|**_stprintf_p_l –**|**_sprintf_p_l**|**_sprintf_p_l**|**_swprintf_p_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_sprintf_p –**, **_sprintf_p_l –**|\<stdio.h>|
|**_swprintf_p –**, **_swprintf_p_l –**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_sprintf_p.c
// This program uses _sprintf_p to format various
// data and place them in the string named buffer.
//

#include <stdio.h>

int main( void )
{
    char     buffer[200],
            s[] = "computer", c = 'l';
    int      i = 35,
            j;
    float    fp = 1.7320534f;

    // Format and print various data:
    j  = _sprintf_p( buffer, 200,
                     "   String:    %s\n", s );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Character: %c\n", c );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Integer:   %d\n", i );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Real:      %f\n", fp );

    printf( "Output:\n%s\ncharacter count = %d\n",
            buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example"></a>Příklad

```C
// crt_swprintf_p.c
// This is the wide character example which
// also demonstrates _swprintf_p returning
// error code.
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    wchar_t buffer[BUFFER_SIZE];
    int     len;

    len = _swprintf_p(buffer, BUFFER_SIZE, L"%2$s %1$d",
                      0, L" marbles in your head.");
    _printf_p( "Wrote %d characters\n", len );

    // _swprintf_p fails because string contains WEOF (\xffff)
    len = _swprintf_p(buffer, BUFFER_SIZE, L"%s",
                      L"Hello\xffff world" );
    _printf_p( "Wrote %d characters\n", len );
}
```

```Output
Wrote 24 characters
Wrote -1 characters
```

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
[printf_p – poziční parametry](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
