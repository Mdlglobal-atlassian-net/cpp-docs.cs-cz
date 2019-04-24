---
title: _get_printf_count_output
ms.date: 11/04/2016
apiname:
- _get_printf_count_output
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
- get_printf_count_output
- _get_printf_count_output
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
ms.openlocfilehash: 477e4a9e987f27bd70b9707e91b9ea9d84b69993
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332050"
---
# <a name="getprintfcountoutput"></a>_get_printf_count_output

Určuje, zda [printf _printf_l –, wprintf _wprintf_l –](printf-printf-l-wprintf-wprintf-l.md)– řada funkcí podporu **%n** formátu.

## <a name="syntax"></a>Syntaxe

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>Návratová hodnota

Pokud non-zero **%n** je podporován, 0, pokud **%n** se nepodporuje.

## <a name="remarks"></a>Poznámky

Pokud **%n** je nepodporované (výchozí), zjištění **%n** ve formátovacím řetězci u všech **printf** funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud **%n** je povolena podpora (viz [_set_printf_count_output –](set-printf-count-output.md)) pak **%n** budou chovat, jak je popsáno v [syntaxe specifikace formátu: printf a wprintf Funkce](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_set_printf_count_output –](set-printf-count-output.md).

## <a name="see-also"></a>Viz také:

[_set_printf_count_output](set-printf-count-output.md)<br/>
