---
title: tmpfile_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 57c230dedd3415a272e168b586a16ccb03f5d29a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="tmpfiles"></a>tmpfile_s

Vytvoří dočasný soubor. Je verzi [tmpfile –](tmpfile.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t tmpfile_s(
   FILE** pFilePtr
);
```

### <a name="parameters"></a>Parametry

*pFilePtr*<br/>
Adresa ukazatel k uložení adresu generovaného ukazatele na datový proud.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud bylo úspěšné, kód chyby při selhání.

### <a name="error-conditions"></a>Chybové stavy

|*pFilePtr*|**Návratová hodnota**|**Obsah***pFilePtr* |
|----------------|----------------------|---------------------------------|
|**HODNOTU NULL**|**EINVAL –**|nebyl změněn.|

Pokud dojde k chybě ověření výše uvedených parametrů, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –** a že návratová hodnota **einval –**.

## <a name="remarks"></a>Poznámky

**Tmpfile_s –** funkce vytvoří dočasný soubor a vloží do tohoto datového proudu v ukazatel *pFilePtr* argument. Dočasný soubor se vytvoří v kořenovém adresáři. Chcete-li vytvořit dočasný soubor v adresáři, než je kořenový adresář, použijte [tmpnam_s –](tmpnam-s-wtmpnam-s.md) nebo [tempnam –](tempnam-wtempnam-tmpnam-wtmpnam.md) ve spojení s [fopen –](fopen-wfopen.md).

Pokud soubor nelze otevřít, **tmpfile_s –** zapíše **NULL** k *pFilePtr* parametr. Toto dočasný soubor bude odstraněn automaticky při zavření souboru, když program ukončí normálně, nebo když **_rmtmp –** je volána, za předpokladu, že aktuální pracovní adresář se nemění. Dočasný soubor je otevřen v **w + b** režimu (binární čtení a zápis).

Selhání může dojít, pokud se pokusíte více než **TMP_MAX_S** (viz STDIO. H) volání s **tmpfile_s –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

> [!NOTE]
> V tomto příkladu může vyžadovat administrativní oprávnění ke spouštění v systému Windows.

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

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
