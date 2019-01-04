---
title: _setmode
ms.date: 11/04/2016
apiname:
- _setmode
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
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: 67cca27ba03a99d7e192d438a98f1bb3a93845ee
ms.sourcegitcommit: cce52b2232b94ce8fd8135155b86e2d38a4e4562
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2019
ms.locfileid: "54031275"
---
# <a name="setmode"></a>_setmode

Nastaví režim překladu souboru.

## <a name="syntax"></a>Syntaxe

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Popisovač souboru.

*Režim*<br/>
Nový režim překladu.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí předchozí režim překladu.

Pokud jsou předány neplatné parametry pro tuto funkci, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce vrátí hodnotu -1 a nastaví **errno** buď **EBADF**, což znamená neplatného popisovače souboru, nebo **EINVAL**, který Určuje neplatnou *režimu* argument.

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Setmode** funkce nastaví *režimu* režim překladu souboru Dal *fd*. Předání **_O_TEXT** jako *režimu* nastaví text (který je, přeloženém) režimu. Návrat na začátek řádku return-line informačního kanálu kombinace (CR-LF) jsou přeloženy do jednoho kanálu znak na vstupním řádku. Znaky informačního kanálu řádků jsou přeloženy do na výstupu jako kombinace CR-LF. Předání **_O_BINARY** sady binárním (nepřeloženém) režimu, ve kterém jsou tyto překlady potlačeny.

Můžete také předat **_O_U16TEXT**, **_O_U8TEXT**, nebo **_O_WTEXT** pro povolení režimu Unicode, jak je uvedeno v druhém příkladu dále v tomto dokumentu.

> [!CAUTION]
> Režim kódování Unicode je pro funkce široký tisku (například `wprintf`) a není podporována pro úzké funkce tisku. Použití funkce úzký tisk v režimu datového proudu Unicode aktivuje assert.

**_setmode** se obvykle používá k úpravě výchozí režim překladu **stdin** a **stdout**, ale můžete ji použít na jakýkoli soubor. Pokud použijete **_setmode** pro popisovače souborů pro datový proud, volejte **_setmode** před provedením jakékoli operace vstupní nebo výstupní v datovém proudu.

> [!CAUTION]
> Pokud zapíšete data do datového proudu souboru explicitně vyprázdnění kód pomocí [fflush –](fflush.md) před použitím **_setmode** ke změně režimu. Pokud není vyprázdnění kód, může se zobrazit neočekávané chování. Pokud jste nenapsali data do datového proudu, není nutné vyprázdnit kód.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|-------------|---------------------|----------------------|
|**_setmode**|\<IO.h >|\<fcntl.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
