---
title: _fileno – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _fileno
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
- _fileno
dev_langs:
- C++
helpviewer_keywords:
- file handles [C++], getting from streams
- fileno function
- _fileno function
- streams, getting file handles
ms.assetid: 86474174-2f17-4100-bcc4-352dd976c7b5
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9eb3950ce66f6bfeadd4cc25602ffe2f6abda409
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="fileno"></a>_fileno

Získá popisovače souborů, které jsou přidružené k datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int _fileno(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Datový proud*<br/>
Ukazatel **souboru** struktura.

## <a name="return-value"></a>Návratová hodnota

**_fileno –** vrátí popisovač souboru. Neexistuje žádný návratový chyby. Pokud není definován výsledek *datového proudu* neurčuje soubor otevřený. Pokud datový proud je **NULL**, **_fileno –** volá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, tato funkce vrátí hodnotu -1 a nastaví je povoleno spuštění **errno** k **einval –**.

Další informace o těchto a dalších kódy chyb najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

> [!NOTE]
> Pokud **stdout** nebo **stderr** není spojen s výstupní proud (například v aplikaci Windows bez okna konzoly), je popisovače souborů vrátil -2. V předchozích verzích byla popisovače souborů, vrátí hodnotu -1. Tato změna umožňuje aplikacím rozlišit tuto podmínku z k chybě.

## <a name="remarks"></a>Poznámky

**_Fileno –** rutina vrátí popisovače souborů, které jsou aktuálně přidružen *datového proudu*. Tato rutina je implementováno jako funkce i jako makra. Informace o výběru buď implementace najdete v tématu [výběru mezi funkcemi a makry](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fileno**|\<stdio.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fileno.c
// This program uses _fileno to obtain
// the file descriptor for some standard C streams.
//

#include <stdio.h>

int main( void )
{
   printf( "The file descriptor for stdin is %d\n", _fileno( stdin ) );
   printf( "The file descriptor for stdout is %d\n", _fileno( stdout ) );
   printf( "The file descriptor for stderr is %d\n", _fileno( stderr ) );
}
```

```Output
The file descriptor for stdin is 0
The file descriptor for stdout is 1
The file descriptor for stderr is 2
```

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
