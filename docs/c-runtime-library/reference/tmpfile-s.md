---
title: tmpfile_s
ms.date: 11/04/2016
apiname:
- tmpfile_s
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
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 341e1c8ed6dd20ec7e6a3d71999fb365e45e614a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155573"
---
# <a name="tmpfiles"></a>tmpfile_s

Vytvoří dočasný soubor. Jedná se verzi [tmpfile –](tmpfile.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t tmpfile_s(
   FILE** pFilePtr
);
```

### <a name="parameters"></a>Parametry

*pFilePtr*<br/>
Adresa ukazatele k ukládání adresy generované ukazatel na datový proud.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je úspěšná, kód chyby při selhání.

### <a name="error-conditions"></a>Chybové podmínky

|*pFilePtr*|**Návratová hodnota**|**Obsah***pFilePtr*|
|----------------|----------------------|---------------------------------|
|**NULL**|**EINVAL**|nebyl změněn.|

Pokud dojde k chybě ověření výše uvedených parametrů, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a vrácená hodnota je **EINVAL**.

## <a name="remarks"></a>Poznámky

**Tmpfile_s –** funkce vytvoří dočasný soubor a umístí ukazatel na tento datový proud *pFilePtr* argument. Dočasný soubor se vytvoří v kořenovém adresáři. Chcete-li vytvořit dočasný soubor v jiný adresář než kořenový, použijte [tmpnam_s –](tmpnam-s-wtmpnam-s.md) nebo [tempnam –](tempnam-wtempnam-tmpnam-wtmpnam.md) ve spojení s [fopen](fopen-wfopen.md).

Pokud soubor nejde otevřít, **tmpfile_s –** zapíše **NULL** k *pFilePtr* parametru. Tento dočasný soubor automaticky odstraní při zavření souboru, když program skončí normálně, ani když **_rmtmp –** je volána, za předpokladu, že aktuální pracovní adresář nezmění. Dočasný soubor je otevřen v **w + b** režimu (binární čtení a zápis).

Selhání může dojít, pokud při pokusu o více než **TMP_MAX_S** (viz STDIO. H) volání s **tmpfile_s –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

> [!NOTE]
> V tomto příkladu může vyžadovat oprávnění správce pro spuštění na Windows.

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

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
