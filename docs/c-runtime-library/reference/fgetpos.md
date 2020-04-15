---
title: fgetpos
ms.date: 4/2/2020
api_name:
- fgetpos
- _o_fgetpos
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
- fgetpos
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
ms.openlocfilehash: 0c16150a6240068e1453ec90b396c87ab9ece5a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346915"
---
# <a name="fgetpos"></a>fgetpos

Získá indikátor pozice souboru datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int fgetpos(
   FILE *stream,
   fpos_t *pos
);
```

### <a name="parameters"></a>Parametry

*Proudu*<br/>
Cílový proud.

*Pos*<br/>
Skladování indikátoru polohy.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, **fgetpos** vrátí 0. Při selhání vrátí nenulovou hodnotu a nastaví **errno** na jednu z následujících konstant manifestu (definované v STDIO. H): **EBADF**, což znamená, že zadaný datový proud není platný ukazatel souboru nebo není přístupný, nebo **EINVAL**, což znamená, že hodnota *datového proudu* nebo hodnota *pos* je neplatná, například pokud je nulový ukazatel. Pokud *je datový proud* nebo *pos* ukazatelem **NULL,** funkce vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Poznámky

Funkce **fgetpos** získá aktuální hodnotu indikátoru pozice souboru argumentu *datového proudu* a uloží jej do objektu, na který se vztahuje *pos*. Funkce **fsetpos** může později použít informace uložené v *pos* k obnovení ukazatele *argumentu datového proudu* na jeho pozici v době, kdy byl volán **fgetpos.** Hodnota *pos* je uložena ve vnitřním formátu a je určena pouze pro **fgetpos** a **fsetpos**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fgetpos**|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fgetpos.c
// This program uses fgetpos and fsetpos to
// return to a location in a file.

#include <stdio.h>

int main( void )
{
   FILE   *stream;
   fpos_t pos;
   char   buffer[20];

   if( fopen_s( &stream, "crt_fgetpos.txt", "rb" ) ) {
      perror( "Trouble opening file" );
      return -1;
   }

   // Read some data and then save the position.
   fread( buffer, sizeof( char ), 8, stream );
   if( fgetpos( stream, &pos ) != 0 ) {
      perror( "fgetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fgetpos: %.13s\n", buffer );

   // Restore to old position and read data
   if( fsetpos( stream, &pos ) != 0 ) {
      perror( "fsetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fsetpos: %.13s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crt_fgetpostxt"></a>Vstup: crt_fgetpos.txt

```Input
fgetpos gets a stream's file-position indicator.
```

### <a name="output-crt_fgetpostxt"></a>Výstup crt_fgetpos.txt

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
