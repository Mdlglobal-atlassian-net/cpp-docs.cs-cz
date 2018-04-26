---
title: _setmode – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 44b17b7b6fe579d9266c98aeb410b30b94f9b136
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
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

V případě úspěchu vrátí předchozí režim překladu.

Pokud k této funkci jsou předány neplatné parametry, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, tato funkce vrátí hodnotu -1 a nastaví je povoleno spuštění **errno** buď **ebadf –**, což naznačuje popisovač souboru je neplatný nebo **einval –**, které Určuje neplatnou *režimu* argument.

Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Setmode –** funkce se nastaví na *režimu* režim překladu souboru poskytují *fd*. Předávání **_o_text –** jako *režimu* nastaví text, (který se převést) režimu. Kombinace informačního kanálu (CR-LF) znaků CR vrátit line se přeložit na jeden řádek kanálu znak na vstup. Řádek informačního kanálu znaky jsou převedeny na znaky CR LF kombinace na výstup. Předávání **_o_binary –** nastaví binární (nepřeložený) režim, ve které jsou potlačovány tyto překladů.

Můžete také předat **_O_U16TEXT**, **_O_U8TEXT**, nebo **_O_WTEXT** chcete povolit režim Unicode, jak je předvedeno v druhém příkladu dále v tomto dokumentu. **_setmode –** se obvykle používá k úpravě výchozí režim překladu **stdin –** a **stdout**, ale můžete ji použít na všechny soubory. Pokud použijete **_setmode –** do popisovače souboru pro datový proud, volání **_setmode –** před provedením jakékoli operace vstupních nebo výstupních v datovém proudu.

> [!CAUTION]
> Pokud jste zapisovat data do datového proudu souboru, explicitně vyprázdnit kód pomocí [fflush –](fflush.md) před použitím **_setmode –** ke změně režimu. Pokud není vyprázdnění kód, může získat neočekávanému chování. Pokud nebyly zapisovat data do datového proudu, nemáte vyprázdnění kód.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|
|-------------|---------------------|----------------------|
|**_setmode**|\<IO.h >|\<fcntl.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
