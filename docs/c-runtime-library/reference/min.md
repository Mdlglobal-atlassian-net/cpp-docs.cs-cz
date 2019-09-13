---
title: __min
ms.date: 04/05/2018
api_name:
- __min
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
- __min
- min
- _min
helpviewer_keywords:
- __min macro
- min macro
- minimum macro
- _min macro
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
ms.openlocfilehash: 6b5cc6517c125f91337ca0d9b12b7a49bd7c1753
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951739"
---
# <a name="__min"></a>__min

Makro preprocesoru, které vrací menší ze dvou hodnot.

## <a name="syntax"></a>Syntaxe

```C
#define __min(a,b) (((a) < (b)) ? (a) : (b))
```

### <a name="parameters"></a>Parametry

*a*, *b*<br/>
Hodnoty libovolného typu, na kterém **<** operátor pracuje.

## <a name="return-value"></a>Návratová hodnota

Menší ze dvou argumentů.

## <a name="remarks"></a>Poznámky

Makro **__min** porovná dvě hodnoty a vrátí hodnotu menšího typu. Argumenty mohou být libovolného číselného datového typu, podepsán nebo bez znaménka. Oba argumenty i návratová hodnota musí být stejného datového typu.

Vrácený argument je vyhodnocen dvakrát makrem. To může vést k neočekávaným výsledkům, pokud je argument výraz, který při vyhodnocení změní jeho hodnotu, například `*p++`.

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

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[__max](max.md)<br/>
