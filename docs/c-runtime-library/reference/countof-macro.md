---
title: _countof – makro
ms.date: 03/22/2018
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
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
ms.openlocfilehash: 60b4350d6cf14a545de67de0bdaee70ee2099006
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335344"
---
# <a name="countof-macro"></a>_countof – makro

Vypočítá počet prvků v poli staticky přiřazované.

## <a name="syntax"></a>Syntaxe

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>Parametry

*Pole*<br/>
Název pole.

## <a name="return-value"></a>Návratová hodnota

Počet prvků v poli, vyjádřené jako **size_t**.

## <a name="remarks"></a>Poznámky

**_countof** je implementovaný jako preprocesorové makro podobné funkce. Verze C++ obsahuje další šablony strojů k detekci v době kompilace, pokud je předán ukazatel místo staticky deklarovaným pole.

Ujistěte se, že *pole* je ve skutečnosti pole, nikoli ukazatel. V jazyce C **_countof** vytváří chybné výsledky, pokud *pole* ukazatel. V C++, **_countof** nejde zkompilovat, pokud *pole* ukazatel.  Pole předána jako parametr funkce *decays na ukazatel*, což znamená, že v rámci této funkce nelze použít **_countof** k určení rozsahu objektu array.

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
