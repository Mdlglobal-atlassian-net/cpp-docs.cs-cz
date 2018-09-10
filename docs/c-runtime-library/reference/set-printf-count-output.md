---
title: _set_printf_count_output – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_printf_count_output
- _set_printf_count_output
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 783225412b01430d1043dafd4761cb7432eaa1d7
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108316"
---
# <a name="setprintfcountoutput"></a>_set_printf_count_output

Povolit nebo zakázat podporu **%n** formátu [printf _printf_l –, wprintf _wprintf_l –](printf-printf-l-wprintf-wprintf-l.md)-řady funkcí.

## <a name="syntax"></a>Syntaxe

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>Parametry

*Povolit*<br/>
Nenulové hodnoty povolit **%n** podporovat, 0 pro vypnutí **%n** podporovat.

## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

Stav **%n** podporovat před voláním této funkce: Pokud nenulové **%n** byla povolená podpora, 0, pokud byla zakázána.

## <a name="remarks"></a>Poznámky

Z důvodů zabezpečení, podpora **%n** specifikátor formátu je ve výchozím nastavení zakázána **printf** a jeho variant. Pokud **%n** dochází v **printf** specifikace formátu, výchozí chování je vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Volání **_set_printf_count_output –** s argumentem nenulové způsobí **printf**-produktovou řadu funkcí pro interpretaci **%n** jak je popsáno v [formátu Syntaxe specifikace: funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_printf_count_output**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_set_printf_count_output.c
#include <stdio.h>

int main()
{
   int e;
   int i;
   e = _set_printf_count_output( 1 );
   printf( "%%n support was %sabled.\n",
        e ? "en" : "dis" );
   printf( "%%n support is now %sabled.\n",
        _get_printf_count_output() ? "en" : "dis" );
   printf( "12345%n6789\n", &i ); // %n format should set i to 5
   printf( "i = %d\n", i );
}
```

```Output
%n support was disabled.
%n support is now enabled.
123456789
i = 5
```

## <a name="see-also"></a>Viz také:

[_get_printf_count_output](get-printf-count-output.md)<br/>
