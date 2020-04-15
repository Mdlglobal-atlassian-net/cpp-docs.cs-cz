---
title: tmpfile_s
ms.date: 4/2/2020
api_name:
- tmpfile_s
- _o_tmpfile_s
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
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 8f9dd58abdf1d3225341e40661c14ae3a5013257
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362465"
---
# <a name="tmpfile_s"></a>tmpfile_s

Vytvoří dočasný soubor. Jedná se o verzi [souboru tmpfile](tmpfile.md) s vylepšeními zabezpečení, jak je popsáno v [části Funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t tmpfile_s(
   FILE** pFilePtr
);
```

### <a name="parameters"></a>Parametry

*pFilePtr*<br/>
Adresa ukazatele pro uložení adresy generovaného ukazatele do datového proudu.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je úspěšná, kód chyby při selhání.

### <a name="error-conditions"></a>Chybové stavy

|*pFilePtr*|**Návratová hodnota**|**Obsah**  *pFilePtr*|
|----------------|----------------------|---------------------------------|
|**Null**|**EINVAL**|se nezměnilo|

Pokud dojde k chybě ověření výše uvedeného parametru, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **errno** je nastavena na **EINVAL** a vrácená hodnota je **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **tmpfile_s** vytvoří dočasný soubor a umístí ukazatel na tento datový proud v argumentu *pFilePtr.* Dočasný soubor je vytvořen v kořenovém adresáři. Chcete-li vytvořit dočasný soubor v jiném adresáři než v kořenovém adresáři, použijte [tmpnam_s](tmpnam-s-wtmpnam-s.md) nebo [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) ve spojení s [fopen](fopen-wfopen.md).

Pokud soubor nelze otevřít, **tmpfile_s** zapíše **hodnotu NULL** do parametru *pFilePtr.* Tento dočasný soubor je automaticky odstraněn při zavření souboru, při ukončení programu normálně, nebo **při _rmtmp** je volána, za předpokladu, že aktuální pracovní adresář nezmění. Dočasný soubor je otevřen v **režimu w+b** (binární čtení a zápis).

Selhání může dojít, pokud se pokusíte více než **TMP_MAX_S** (viz STDIO. H) volá s **tmpfile_s**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

> [!NOTE]
> Tento příklad může vyžadovat oprávnění správce ke spuštění v systému Windows.

```C
// crt_tmpfile_s.c
// This program uses tmpfile_s to create a
// temporary file, then deletes this file with _rmtmp.
//

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char tempstring[] = "String to be written";
   int  i;
   errno_t err;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      err = tmpfile_s(&stream);
      if( err )
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

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
