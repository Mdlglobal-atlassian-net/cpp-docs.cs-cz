---
title: __min – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __min
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
- __min
- min
- _min
dev_langs:
- C++
helpviewer_keywords:
- __min macro
- min macro
- minimum macro
- _min macro
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0cc69cb018cda6fc093c570dab86a8df4cf396b7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="min"></a>__min

Makro preprocesoru, který vrací menší ze dvou hodnot.

## <a name="syntax"></a>Syntaxe

```C
#define __min(a,b) (((a) < (b)) ? (a) : (b))
```

### <a name="parameters"></a>Parametry

*a*, *b*<br/>
Zadejte hodnoty všech, který **<** operátor funguje na.

## <a name="return-value"></a>Návratová hodnota

Menší dva argumenty.

## <a name="remarks"></a>Poznámky

**__Min –** makro porovná dvě hodnoty a vrátí hodnotu typu menší. Argumenty, které může být jakékoli číselný datový typ, podepsané nebo bez znaménka. Argumenty a návratová hodnota musí být stejného datového typu.

Argument vrátil je vyhodnocován dvakrát makro. To může vést k neočekávaným výsledkům, pokud je argument výraz, který mění jeho hodnota při vyhodnotí, jako například `*p++`.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**__min**|\<stdlib.h>|

## <a name="example"></a>Příklad

```C
// crt_minmax.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int a = 10;
   int b = 21;

   printf( "The larger of %d and %d is %d\n",  a, b, __max( a, b ) );
   printf( "The smaller of %d and %d is %d\n", a, b, __min( a, b ) );
}
```

```Output
The larger of 10 and 21 is 21
The smaller of 10 and 21 is 10
```

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[__max](max.md)<br/>
