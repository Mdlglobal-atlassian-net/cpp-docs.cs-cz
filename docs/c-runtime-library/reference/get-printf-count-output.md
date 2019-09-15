---
title: _get_printf_count_output
ms.date: 11/04/2016
api_name:
- _get_printf_count_output
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
- get_printf_count_output
- _get_printf_count_output
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
ms.openlocfilehash: 15b37ac759821ad56cc5c03c9b98719d8f0cc19a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955711"
---
# <a name="_get_printf_count_output"></a>_get_printf_count_output

Označuje, zda funkce [printf, _printf_l, wprintf a _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-Family podporují formát **% n** .

## <a name="syntax"></a>Syntaxe

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je podporováno **% n** , 0, pokud není podporováno **% n** .

## <a name="remarks"></a>Poznámky

Pokud **% n** není podporován (výchozí), se kterým se zaznamená **% n** ve formátovacím řetězci jakékoli **printf** funkce, vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud je povolena podpora **% n** (viz [_set_printf_count_output](set-printf-count-output.md)), pak se **% n** bude chovat, jak je popsáno v [syntaxi specifikace formátu: printf a wprintf Functions](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_set_printf_count_output](set-printf-count-output.md).

## <a name="see-also"></a>Viz také:

[_set_printf_count_output](set-printf-count-output.md)<br/>
