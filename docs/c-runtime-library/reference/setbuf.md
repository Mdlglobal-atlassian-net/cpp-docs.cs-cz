---
title: setbuf – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- setbuf
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
- setbuf
dev_langs:
- C++
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7a88ac98b8226b51ad036a0e31c919db9a63a0a0
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="setbuf"></a>setbuf

Ovládací prvky datového proudu do vyrovnávací paměti. Tato funkce je zastaralé; použít [setvbuf –](setvbuf.md) místo.

## <a name="syntax"></a>Syntaxe

```C
void setbuf(
   FILE *stream,
   char *buffer
);
```

### <a name="parameters"></a>Parametry

*datový proud* ukazatel na **souboru** struktura.

*vyrovnávací paměť* uživatel přidělené vyrovnávací paměti.

## <a name="remarks"></a>Poznámky

**Setbuf –** funkce ukládání do vyrovnávací paměti pro ovládací prvky *datového proudu*. *Datového proudu* argument musí odkazovat na soubor otevřete, který nebyl číst nebo zapisovat. Pokud *vyrovnávací paměti* argument je **NULL**, datový proud je zrušení ve vyrovnávací paměti. Pokud ne, vyrovnávací paměti musí odkazovat na pole znaků délky **bufsiz –**, kde **bufsiz –** je velikost vyrovnávací paměti, jak jsou definovány v STDIO. H. Uživatelem zadanou vyrovnávací paměť, místo vyrovnávací paměti výchozí přidělená systémem pro daný datový proud, se používá pro vstupně-výstupní operace ukládání do vyrovnávací paměti. **Stderr** datový proud je zrušení ve vyrovnávací paměti ve výchozím nastavení, ale můžete použít **setbuf –** přiřadit vyrovnávací paměti do **stderr**.

**setbuf –** nahradila [setvbuf –](setvbuf.md), což je upřednostňovaný rutiny pro nový kód. **setbuf –** se zachovává kvůli kompatibilitě s existujícího kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**setbuf**|\<stdio.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_setbuf.c
// compile with: /W3
// This program first opens files named DATA1 and
// DATA2. Then it uses setbuf to give DATA1 a user-assigned
// buffer and to change DATA2 so that it has no buffer.

#include <stdio.h>

int main( void )
{
   char buf[BUFSIZ];
   FILE *stream1, *stream2;

   fopen_s( &stream1, "data1", "a" );
   fopen_s( &stream2, "data2", "w" );

   if( (stream1 != NULL) && (stream2 != NULL) )
   {
      // "stream1" uses user-assigned buffer:
      setbuf( stream1, buf ); // C4996
      // Note: setbuf is deprecated; consider using setvbuf instead
      printf( "stream1 set to user-defined buffer at: %Fp\n", buf );

      // "stream2" is unbuffered
      setbuf( stream2, NULL ); // C4996
      printf( "stream2 buffering disabled\n" );
      _fcloseall();
   }
}
```

```Output
stream1 set to user-defined buffer at: 0012FCDC
stream2 buffering disabled
```

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setvbuf](setvbuf.md)<br/>
