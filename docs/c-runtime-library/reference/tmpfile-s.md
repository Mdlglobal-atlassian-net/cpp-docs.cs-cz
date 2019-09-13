---
title: tmpfile_s
ms.date: 11/04/2016
api_name:
- tmpfile_s
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
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 64107f26fa651739f4d5bdd7521b15d9d458df65
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946059"
---
# <a name="tmpfile_s"></a>tmpfile_s

Vytvoří dočasný soubor. Jedná se o verzi [tmpfile](tmpfile.md) s vylepšením zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t tmpfile_s(
   FILE** pFilePtr
);
```

### <a name="parameters"></a>Parametry

*pFilePtr*<br/>
Adresa ukazatele pro uložení adresy vygenerovaného ukazatele do datového proudu.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je úspěšná, kód chyby při selhání.

### <a name="error-conditions"></a>Chybové stavy

|*pFilePtr*|**Návratová hodnota**|**Obsah** *pFilePtr*|
|----------------|----------------------|---------------------------------|
|**NULL**|**EINVAL**|nezměněno|

Pokud dojde k chybě ověření výše uvedeného parametru, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a návratová hodnota je **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **tmpfile_s** vytvoří dočasný soubor a do argumentu *pFilePtr* vloží ukazatel na tento datový proud. Dočasný soubor se vytvoří v kořenovém adresáři. Chcete-li vytvořit dočasný soubor v jiném než kořenovém adresáři, použijte [tmpnam_s](tmpnam-s-wtmpnam-s.md) nebo [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) ve spojení s [fopen](fopen-wfopen.md).

Pokud soubor nelze otevřít, **tmpfile_s** zapíše **hodnotu null** do parametru *pFilePtr* . Tento dočasný soubor se automaticky odstraní při zavření souboru, když se program normálně ukončí, nebo když se zavolá **_rmtmp** . za předpokladu, že se aktuální pracovní adresář nemění. Dočasný soubor je otevřen v režimu **w + b** (binární režim pro čtení a zápis).

K selhání může dojít, pokud se pokusíte o více než **TMP_MAX_S** (viz stdio. H) volání s **tmpfile_s**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
