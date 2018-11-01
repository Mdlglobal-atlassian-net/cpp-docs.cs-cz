---
title: _isatty
ms.date: 11/04/2016
apiname:
- _isatty
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
- _isatty
helpviewer_keywords:
- isatty function
- character device checking
- _isatty function
- checking character devices
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
ms.openlocfilehash: ef0df5f859779c081df47ef4bfe938ec2601d524
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545584"
---
# <a name="isatty"></a>_isatty

Určuje, zda je soubor popisovač spojen se znakovým zařízením.

## <a name="syntax"></a>Syntaxe

```C
int _isatty( int fd );
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Popisovač souboru odkazující na testované zařízení.

## <a name="return-value"></a>Návratová hodnota

**_isatty –** vrací nenulovou hodnotu, pokud je popisovač spojen se znakovým zařízením. V opačném případě **_isatty –** vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

**_Isatty –** funkce určuje, zda *fd* souvisí se znakovým zařízením (terminál, konzole, tiskárna nebo sériový port).

Tato funkce ověřuje *fd* parametru. Pokud *fd* je nesprávný ukazatel souboru, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, funkce vrátí hodnotu 0 a nastaví **errno** k **EBADF**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_isatty**|\<IO.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_isatty.c
/* This program checks to see whether
* stdout has been redirected to a file.
*/

#include <stdio.h>
#include <io.h>

int main( void )
{
   if( _isatty( _fileno( stdout ) ) )
      printf( "stdout has not been redirected to a file\n" );
   else
      printf( "stdout has been redirected to a file\n");
}
```

### <a name="sample-output"></a>Vzorový výstup

```Output
stdout has not been redirected to a file
```

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
