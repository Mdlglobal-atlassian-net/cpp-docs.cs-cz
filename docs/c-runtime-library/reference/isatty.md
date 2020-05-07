---
title: _isatty
ms.date: 4/2/2020
api_name:
- _isatty
- _o__isatty
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _isatty
helpviewer_keywords:
- isatty function
- character device checking
- _isatty function
- checking character devices
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
ms.openlocfilehash: 16d67053cd05d567e4c732d4366bd121863d43f9
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919773"
---
# <a name="_isatty"></a>_isatty

Určuje, zda je popisovač souboru přidružen ke znakovým zařízením.

## <a name="syntax"></a>Syntaxe

```C
int _isatty( int fd );
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Popisovač souboru, který odkazuje na zařízení, které se má testovat

## <a name="return-value"></a>Návratová hodnota

**_isatty** vrátí nenulovou hodnotu, pokud je popisovač přidružen ke znakovým zařízením. V opačném případě **_isatty** vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

Funkce **_isatty** určuje, zda je *FD* přidružen ke znakovým zařízením (terminál, konzola, tiskárna nebo sériový port).

Tato funkce ověří parametr *FD* . Pokud je *FD* špatný ukazatel na soubor, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí funkce hodnotu 0 a nastaví **errno** na **EBADF**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_isatty**|\<IO. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
