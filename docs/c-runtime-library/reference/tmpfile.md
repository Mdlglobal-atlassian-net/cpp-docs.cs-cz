---
title: tmpfile
ms.date: 11/04/2016
apiname:
- tmpfile
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
- tmpfile
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
ms.openlocfilehash: 98afcb7a3e04a96a1b08bc1b975634153e550839
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155560"
---
# <a name="tmpfile"></a>tmpfile

Vytvoří dočasný soubor. Tato funkce je zastaralá, protože bezpečnější verze je k dispozici. Zobrazit [tmpfile_s –](tmpfile-s.md).

## <a name="syntax"></a>Syntaxe

```C
FILE *tmpfile( void );
```

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného ověření **tmpfile –** vrátí ukazatel streamu. V opačném případě vrátí **NULL** ukazatele.

## <a name="remarks"></a>Poznámky

**Tmpfile –** funkce vytvoří dočasný soubor a vrátí ukazatel na tento stream. Dočasný soubor se vytvoří v kořenovém adresáři. Chcete-li vytvořit dočasný soubor v jiný adresář než kořenový, použijte [tmpnam –](tempnam-wtempnam-tmpnam-wtmpnam.md) nebo [tempnam –](tempnam-wtempnam-tmpnam-wtmpnam.md) ve spojení s [fopen](fopen-wfopen.md).

Pokud soubor nejde otevřít, **tmpfile –** vrátí **NULL** ukazatele. Tento dočasný soubor automaticky odstraní při zavření souboru, když program skončí normálně, ani když **_rmtmp –** je volána, za předpokladu, že aktuální pracovní adresář nezmění. Dočasný soubor je otevřen v **w + b** režimu (binární čtení a zápis).

Selhání může dojít, pokud při pokusu o více než TMP_MAX (viz STDIO. H) volání s **tmpfile –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**tmpfile**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

> [!NOTE]
> Tento příklad vyžaduje oprávnění správce pro spuštění v systému Windows Vista.

```C
// crt_tmpfile.c
// compile with: /W3
// This program uses tmpfile to create a
// temporary file, then deletes this file with _rmtmp.
#include <stdio.h>

int main( void )
{
   FILE *stream;
   int  i;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      if( (stream = tmpfile()) == NULL ) // C4996
      // Note: tmpfile is deprecated; consider using tmpfile_s instead
         perror( "Could not open new temporary file\n" );
      else
         printf( "Temporary file %d was created\n", i );
   }

   // Remove temporary files.
   printf( "%d temporary files deleted\n", _rmtmp() );
}
```

```Output
Temporary file 1 was created
Temporary file 2 was created
Temporary file 3 was created
3 temporary files deleted
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
