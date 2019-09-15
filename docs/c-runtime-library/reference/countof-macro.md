---
title: _countof – makro
ms.date: 03/22/2018
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
- _countof
- countof
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
ms.openlocfilehash: 3debd63da7d218e29f31847034c69d89b4691643
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942692"
---
# <a name="_countof-macro"></a>_countof – makro

Vypočítá počet prvků ve staticky vyhrazeném poli.

## <a name="syntax"></a>Syntaxe

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>Parametry

*array*<br/>
Název pole.

## <a name="return-value"></a>Návratová hodnota

Počet prvků v poli vyjádřený jako **size_t**.

## <a name="remarks"></a>Poznámky

**_countof** je implementováno jako preprocesorové makro typu ". C++ Verze má přídavná zařízení šablon pro detekci v době kompilace, pokud je předán ukazatel namísto staticky deklarovaného pole.

Ujistěte se, že *pole* je ve skutečnosti pole, nikoli ukazatel. V jazyce C **_countof** vytvoří chybné výsledky, pokud je *pole* ukazatelem. V C++ **_countof** neproběhne kompilace, pokud je *pole* ukazatelem.  Pole předané jako parametr funkci *Decays na ukazatel*, což znamená, že v rámci funkce nelze použít **_countof** k určení rozsahu pole.

## <a name="requirements"></a>Požadavky

|– Makro|Požadovaný hlavičkový soubor|
|-----------|---------------------|
|**_countof**|\<stdlib.h>|

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

## <a name="see-also"></a>Viz také:

[sizeof – operátor](../../cpp/sizeof-operator.md)<br/>
