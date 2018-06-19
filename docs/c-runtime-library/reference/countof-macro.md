---
title: _countof – makro | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
- _countof
- countof
dev_langs:
- C++
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f30df64b045e2af6181d343a4eafb962d22eaa05
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394740"
---
# <a name="countof-macro"></a>_countof – makro

Vypočítá počet prvků v poli se staticky přidělené.

## <a name="syntax"></a>Syntaxe

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>Parametry

*Pole*<br/>
Název pole.

## <a name="return-value"></a>Návratová hodnota

Počet prvků v poli, vyjádřené jako **size_t –**.

## <a name="remarks"></a>Poznámky

**_countof –** je implementovaný jako makro preprocesoru jako funkce. Verze C++ má navíc šablony strojů detekuje v době kompilace, pokud je předán ukazatel místo staticky deklarované pole.

Ujistěte se, že *pole* je ve skutečnosti pole, nikoli ukazatel. V jazyce C **_countof –** vytváří chybné výsledky, pokud *pole* ukazatel. V jazyce C++ **_countof –** nepodaří kompilovat *pole* ukazatel.  Pole, jako parametr předaný funkci *decays na ukazatel*, což znamená, že v rámci funkce, nemůžete použít **_countof –** zjistěte rozsah pole.

## <a name="requirements"></a>Požadavky

|– Makro|Požadovaný hlavičkový soubor|
|-----------|---------------------|
|**_countof –**|\<stdlib.h>|

## <a name="example"></a>Příklad

```cpp
// crt_countof.cpp
#define _UNICODE
#include <stdio.h>
#include <stdlib.h>
#include <tchar.h>

int main( void )
{
   _TCHAR arr[20], *p;
   printf( "sizeof(arr) = %zu bytes\n", sizeof(arr) );
   printf( "_countof(arr) = %zu elements\n", _countof(arr) );
   // In C++, the following line would generate a compile-time error:
   // printf( "%zu\n", _countof(p) ); // error C2784 (because p is a pointer)

   _tcscpy_s( arr, _countof(arr), _T("a string") );
   // unlike sizeof, _countof works here for both narrow- and wide-character strings
}
```

```Output
sizeof(arr) = 40 bytes
_countof(arr) = 20 elements
```

## <a name="see-also"></a>Viz také

[sizeof – operátor](../../cpp/sizeof-operator.md)<br/>
