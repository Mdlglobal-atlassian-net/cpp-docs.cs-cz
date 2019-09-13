---
title: _setmode
ms.date: 11/04/2016
api_name:
- _setmode
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
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: 7f14cc9451b93a9077916b8c650645990ba654a3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948593"
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

*fd*<br/>
Popisovač souboru.

*Mode*<br/>
Nový režim překladu

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí předchozí režim překladu.

Jsou-li do této funkce předány neplatné parametry, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tato funkce hodnotu-1 a nastaví **errno** na buď **EBADF**, což znamená neplatný popisovač souboru, nebo **EINVAL**, který označuje neplatný argument *režimu* .

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_setmode** nastaví *režim* překladu souboru, který je dán souborem *FD*. Předávání **_O_TEXT** jako *režim* nastavuje text (to je přeložený) režim. Kombinace návratového kanálu návratového řádku (CR-LF) jsou přeloženy na jeden znak víceřádkového kanálu na vstupu. Znaky kanálu čáry se ve výstupu překládají na kombinace znaků CR-LF. Předání **_O_BINARY** sady do binárního (nepřeloženého) režimu, ve kterém jsou tyto překlady potlačeny.

Můžete také předat **_O_U16TEXT**, **_O_U8TEXT**nebo **_O_WTEXT** pro povolení režimu Unicode, jak je znázorněno v druhém příkladu dále v tomto dokumentu.

> [!CAUTION]
> Režim kódování Unicode je určen pro funkce pro nejrůznější tisk ( `wprintf`například) a není podporován pro funkce úzkého tisku. Použití funkce úzkého tisku v datovém proudu režimu Unicode aktivuje vyhodnocení.

**_setmode** se obvykle používá k úpravě výchozího režimu překladu **stdin** a **stdout**, ale můžete ho použít v jakémkoli souboru. Pokud **_setmode** použijete pro popisovač souboru pro datový proud, zavolejte **_setmode** před provedením jakékoli operace vstupu nebo výstupu v datovém proudu.

> [!CAUTION]
> Pokud zapisujete data do datového proudu souboru, kód explicitně vyprázdněte pomocí [fflush](fflush.md) před tím, než použijete **_setmode** ke změně režimu. Pokud kód nezaprázdnete, může dojít k neočekávanému chování. Pokud jste do datového proudu nezapsali data, nemusíte tento kód vyprázdnit.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
