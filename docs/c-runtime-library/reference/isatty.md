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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: c9611c2bd55ebc1602a73e4c71518716ea100420
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343907"
---
# <a name="_isatty"></a>_isatty

Určuje, zda je popisovač souboru přidružen k znakovému zařízení.

## <a name="syntax"></a>Syntaxe

```C
int _isatty( int fd );
```

### <a name="parameters"></a>Parametry

*Fd*<br/>
Popisovač souboru, který odkazuje na zařízení, které má být testováno.

## <a name="return-value"></a>Návratová hodnota

**_isatty** vrátí nenulovou hodnotu, pokud je popisovač přidružen k znakovému zařízení. V opačném případě **vrátí _isatty** 0.

## <a name="remarks"></a>Poznámky

Funkce **_isatty** určuje, zda je *fd* přidruženkznakovému zařízení (terminál, konzola, tiskárna nebo sériový port).

Tato funkce ověřuje parametr *fd.* Pokud *fd* je chybný ukazatel souboru, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí 0 a nastaví **errno** na **EBADF**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_isatty**|\<io.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

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
