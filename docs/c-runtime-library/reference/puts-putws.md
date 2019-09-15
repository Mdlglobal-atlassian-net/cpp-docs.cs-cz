---
title: puts, _putws
ms.date: 11/04/2016
api_name:
- _putws
- puts
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _putts
- _putws
- puts
helpviewer_keywords:
- strings [C++], writing
- _putts function
- standard output, writing to
- putws function
- puts function
- putts function
- _putws function
ms.assetid: 32dada12-ed45-40ac-be06-3feeced9ecd6
ms.openlocfilehash: 1cd38678b321853cb229d86f9554bb76efbc84d6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949791"
---
# <a name="puts-_putws"></a>puts, _putws

Zapíše řetězec do **stdout**.

## <a name="syntax"></a>Syntaxe

```C
int puts(
   const char *str
);
int _putws(
   const wchar_t *str
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Výstupní řetězec.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí nezápornou hodnotu. Pokud **operace** vložení selžou, vrátí **EOF**. Pokud **_putws** selžou, vrátí **WEOF**. Pokud je *str* ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce nastaví **errno** na **EINVAL** a vrátí **EOF** nebo **WEOF**.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **vložení** zapisuje *str* do standardního výstupního proudu **stdout**a nahradí ukončovací znak null řetězce (' \ 0 ') znakem nového řádku (' \ 0 ') ve výstupním datovém proudu.

**_putws** je verze s velkým znakem, kterou **přináší**. Tyto dvě funkce se chovají stejně, pokud je datový proud otevřen v režimu ANSI. vložení v současné **době nepodporuje výstup** do datového proudu Unicode.

**_putwch** zapisuje znaky Unicode pomocí aktuálního nastavení národního prostředí konzoly.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_putts**|**zaskladnění**|**zaskladnění**|**_putws**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**zaskladnění**|\<stdio.h>|
|**_putws**|\<stdio.h>|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou, **stdin**, **stdout**a **stderr**, musí být přesměrované před tím, než je funkce modulu runtime jazyka C můžou použít v aplikacích pro UWP. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_puts.c
// This program uses puts to write a string to stdout.

#include <stdio.h>

int main( void )
{
   puts( "Hello world from puts!" );
}
```

### <a name="output"></a>Výstup

```Output
Hello world from puts!
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
