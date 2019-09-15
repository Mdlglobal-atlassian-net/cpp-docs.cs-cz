---
title: _set_printf_count_output
ms.date: 11/04/2016
api_name:
- _set_printf_count_output
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
- set_printf_count_output
- _set_printf_count_output
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
ms.openlocfilehash: 0d53b4e4c56a69582a4eb517fa1a5c9e10cd7d2f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948420"
---
# <a name="_set_printf_count_output"></a>_set_printf_count_output

Povolí nebo zakáže podporu formátu **% n** ve funkcích [printf, _printf_l, wprintf a _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-Family.

## <a name="syntax"></a>Syntaxe

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>Parametry

*aby*<br/>
Nenulová hodnota pro povolení podpory **% n** , 0 pro zakázání podpory **% n** .

## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

Stav podpory **% n** před voláním této funkce: nenulová, pokud byla povolena podpora **% n** , 0, pokud byla zakázána.

## <a name="remarks"></a>Poznámky

Z důvodu zabezpečení je podpora specifikátoru formátu **% n** ve výchozím nastavení zakázána v **printf** a ve všech jeho variantách. Pokud je **% n** zjištěn ve specifikaci formátu **printf** , výchozí chování je vyvolat neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Volání **_set_printf_count_output** s nenulovým argumentem způsobí, že funkce **printf**-Family interpretují **% n** , jak je popsáno v [syntaxi specifikace formátu: printf a wprintf Functions](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_printf_count_output**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
