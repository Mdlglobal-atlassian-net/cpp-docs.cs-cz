---
title: fgetpos
ms.date: 11/04/2016
apiname:
- fgetpos
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
- fgetpos
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
ms.openlocfilehash: e213c9830ffe6edf04b12a80828f14cc48f77524
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658416"
---
# <a name="fgetpos"></a>fgetpos

Získá datový proud Indikátor pozice v souboru.

## <a name="syntax"></a>Syntaxe

```C
int fgetpos(
   FILE *stream,
   fpos_t *pos
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Cílový datový proud.

*POS*<br/>
Indikátor pozice v úložišti.

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného ověření **fgetpos** vrátí hodnotu 0. Při selhání, vrátí nenulovou hodnotu a nastaví **errno** na jednu z následujících manifest konstanty (definované v STDIO. H): **EBADF**, což znamená, že zadaný datový proud není platným souborem ukazatel nebo není přístupný, nebo **EINVAL**, což znamená, že *stream* hodnotu nebo hodnotu *pos* je neplatný, třeba když buď je ukazatel s hodnotou null. Pokud *stream* nebo *pos* je **NULL** ukazatel myši, funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Poznámky

**Fgetpos** funkce získá aktuální hodnotu *stream* Indikátor pozice v souboru argumentu a ukládá ho do objektu odkazované *pos*. **Fsetpos** funkce můžete později použít informace uložené v *pos* resetovat *stream* argumentu ukazatel na pozici v době **fgetpos** byla volána. *Pos* hodnota uložená v interní formát a je určena pro použití pouze **fgetpos** a **fsetpos**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fgetpos**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="input-crtfgetpostxt"></a>Vstup: crt_fgetpos.txt

```Input
fgetpos gets a stream's file-position indicator.
```

### <a name="output-crtfgetpostxt"></a>Výstup crt_fgetpos.txt

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
