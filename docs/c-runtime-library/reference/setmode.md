---
title: _setmode
ms.date: 4/2/2020
api_name:
- _setmode
- _o__setmode
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
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: 36d2130d4039f1f87f7f54fc26ad02cb8d519b4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353837"
---
# <a name="_setmode"></a>_setmode

Nastaví režim překladu souborů.

## <a name="syntax"></a>Syntaxe

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>Parametry

*Fd*<br/>
Popisovač souboru.

*Režimu*<br/>
Nový režim překladu.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí předchozí režim překladu.

Pokud jsou této funkci předány neplatné parametry, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, vrátí tato funkce -1 a nastaví **errno** buď **EBADF**, což znamená neplatný popisovač souboru, nebo **EINVAL**, což znamená argument neplatného *režimu.*

Další informace o těchto a dalších návratových kódech naleznete [v tématech _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_setmode** nastaví *režim* překladu souboru daný *fd*. Předávání **_O_TEXT** jako *režim* nastaví režim textu (tj. přeložený). Kombinace posuvu zpětného řádku vozíku (CR-LF) jsou přeloženy do jednoho znaku posuvu řádku na vstupu. Znaky podávání řádků jsou přeloženy do kombinací CR-LF na výstupu. Předávání **_O_BINARY** nastaví binární (nepřeložený) režim, ve kterém jsou tyto překlady potlačeny.

Můžete také předat **_O_U16TEXT**, **_O_U8TEXT**nebo **_O_WTEXT** povolit režim Unicode, jak je znázorněno v druhém příkladu dále v tomto dokumentu.

> [!CAUTION]
> Režim Unicode je určen pro široké `wprintf`tiskové funkce (například) a není podporován pro úzké tiskové funkce. Použití funkce úzkého tisku v datovém proudu režimu Unicode aktivuje assert.

**_setmode** se obvykle používá k úpravě výchozího režimu překladu **stdin** a **stdout**, ale můžete jej použít v libovolném souboru. Pokud použijete **_setmode** na popisovač souboru pro datový proud, volání **_setmode** před provedením vstupních nebo výstupních operací v datovém proudu.

> [!CAUTION]
> Pokud zapisujete data do datového proudu souborů, explicitně vyprázdněte kód pomocí [fflush](fflush.md) před použitím **_setmode** změnit režim. Pokud kód nevyprázdníte, může dojít k neočekávanému chování. Pokud jste nezapsali data do datového proudu, není třeba vyprázdnit kód.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_setmode.c
// This program uses _setmode to change
// stdin from text mode to binary mode.

#include <stdio.h>
#include <fcntl.h>
#include <io.h>

int main( void )
{
   int result;

   // Set "stdin" to have binary mode:
   result = _setmode( _fileno( stdin ), _O_BINARY );
   if( result == -1 )
      perror( "Cannot set mode" );
   else
      printf( "'stdin' successfully changed to binary mode\n" );
}
```

```Output
'stdin' successfully changed to binary mode
```

## <a name="example"></a>Příklad

```C
// crt_setmodeunicode.c
// This program uses _setmode to change
// stdout to Unicode. Cyrillic and Ideographic
// characters will appear on the console (if
// your console font supports those character sets).

#include <fcntl.h>
#include <io.h>
#include <stdio.h>

int main(void) {
    _setmode(_fileno(stdout), _O_U16TEXT);
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");
    return 0;
}
```

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
