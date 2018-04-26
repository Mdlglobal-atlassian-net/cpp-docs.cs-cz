---
title: _printf_p –, _printf_p_l –, _wprintf_p –, _wprintf_p_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _printf_p
- _wprintf_p
- _printf_p_l
- _wprintf_p_l
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
- wprintf_p
- _wprintf_p
- printf_p_l
- _printf_p
- printf_p
- _wprintf_p_l
- _printf_p_l
- wprintf_p_l
dev_langs:
- C++
helpviewer_keywords:
- printf_p function
- printf_p_l function
- wprintf_p function
- wprintf_p_l function
- _tprintf_p_l function
- _wprintf_p function
- _wprintf_p_l function
- _printf_p function
- tprintf_p_l function
- _printf_p_l function
ms.assetid: 1b7e9ef9-a069-45db-af9d-c2730168322e
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7698181ba23ececc251196702cb76a3b912788e4
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="printfp-printfpl-wprintfp-wprintfpl"></a>_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l

Vytiskne formátovaný výstup do standardního výstupního datového proudu a umožňuje specifikaci pořadí, ve kterém se používají parametry v řetězci formátu.

## <a name="syntax"></a>Syntaxe

```C
int _printf_p(
   const char *format [,
   argument]...
);
int _printf_p_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int _wprintf_p(
   const wchar_t *format [,
   argument]...
);
int _wprintf_p_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>Parametry

*Formát*<br/>
Formát ovládacího prvku.

*Argument*<br/>
Volitelné argumenty

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí počet znaků, vytisknout nebo záporná, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

**_Printf_p –** funkce naformátuje a vytiskne řady znaků a hodnot do standardního výstupního datového proudu **stdout**. Pokud postupovat podle argumenty *formátu* řetězec, *formátu* řetězec musí obsahovat specifikace, které určují formát výstupu pro argumenty (najdete v části [printf_p – poziční parametry](../../c-runtime-library/printf-p-positional-parameters.md)).

Rozdíl mezi **_printf_p –** a **printf_s –** je, že **_printf_p –** podporuje poziční parametry, které umožní určení pořadí, ve kterém jsou argumenty použít ve formátovacím řetězci. Další informace najdete v tématu [printf_p – poziční parametry](../../c-runtime-library/printf-p-positional-parameters.md).

**_wprintf_p –** je verze široká charakterová **_printf_p –**; chovají stejně jako datový proud se při otevření v režimu ANSI. **_printf_p –** nepodporuje aktuálně výstup do proudu kódování UNICODE.

Verze tyto funkce s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.

> [!IMPORTANT]
> Ujistěte se, že *formát* není řetězec definovaný uživatelem.

Pokud *formátu* nebo *argument* jsou **NULL**, nebo formátu řetězec obsahuje neplatné znaky formátování, **_printf_p –** a **_wprintf_p –** funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, funkce vrátí hodnotu -1 a nastaví je povoleno spuštění **errno** k **einval –**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tprintf_p**|**_printf_p**|**_printf_p**|**_wprintf_p**|
|**_tprintf_p_l –**|**_printf_p_l**|**_printf_p_l**|**_wprintf_p_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_printf_p –**, **_printf_p_l –**|\<stdio.h>|
|**_wprintf_p –**, **_wprintf_p_l –**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou, **stdin –**, **stdout**, a **stderr**, musí být přesměrována C běhové funkce mohli používat v aplikacích pro UPW . Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_printf_p.c
// This program uses the _printf_p and _wprintf_p
// functions to choose the order in which parameters
// are used.

#include <stdio.h>

int main( void )
{
   // Positional arguments
   _printf_p( "Specifying the order: %2$s %3$s %1$s %4$s %5$s.\n",
              "little", "I'm", "a", "tea", "pot");

   // Resume arguments
   _wprintf_p( L"Reusing arguments: %1$d %1$d %1$d %1$d\n", 10);

   // Width argument
   _printf_p("Width specifiers: %1$*2$s", "Hello\n", 10);
}
```

```Output
Specifying the order: I'm a little tea pot.
Reusing arguments: 10 10 10 10
Width specifiers:     Hello
```

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)<br/>
[sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
