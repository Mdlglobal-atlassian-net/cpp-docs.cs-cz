---
title: tmpfile
ms.date: 11/04/2016
api_name:
- tmpfile
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
- tmpfile
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
ms.openlocfilehash: f58c23050fe89f84f283c3784a7c0cee72637bf2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957545"
---
# <a name="tmpfile"></a>tmpfile

Vytvoří dočasný soubor. Tato funkce je zastaralá, protože je k dispozici bezpečnější verze; viz [tmpfile_s](tmpfile-s.md).

## <a name="syntax"></a>Syntaxe

```C
FILE *tmpfile( void );
```

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí **tmpfile** ukazatel na datový proud. V opačném případě vrátí ukazatel s **hodnotou null** .

## <a name="remarks"></a>Poznámky

Funkce **tmpfile** vytvoří dočasný soubor a vrátí ukazatel na tento datový proud. Dočasný soubor se vytvoří v kořenovém adresáři. Chcete-li vytvořit dočasný soubor v jiném než kořenovém adresáři, použijte [tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) nebo [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) ve spojení s [fopen](fopen-wfopen.md).

Pokud soubor nelze otevřít, **tmpfile** vrátí ukazatel s **hodnotou null** . Tento dočasný soubor se automaticky odstraní při zavření souboru, když se program normálně ukončí, nebo když se zavolá **_rmtmp** . za předpokladu, že se aktuální pracovní adresář nemění. Dočasný soubor je otevřen v režimu **w + b** (binární režim pro čtení a zápis).

K selhání může dojít, pokud se pokusíte o více než TMP_MAX (viz STDIO. H) volání s **tmpfile**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**tmpfile**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
