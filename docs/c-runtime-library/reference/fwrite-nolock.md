---
title: _fwrite_nolock – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _fwrite_nolock
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
- _fwrite_nolock
- fwrite_nolock
dev_langs:
- C++
helpviewer_keywords:
- fwrite_nolock function
- streams, writing data to
- _fwrite_nolock function
ms.assetid: 2b4ec6ce-742e-4615-8407-44a0a18ec1d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e22f2c281b076e64419686b9f7c058e284cc5532
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397919"
---
# <a name="fwritenolock"></a>_fwrite_nolock

Zapíše data do datového proudu, bez blokování vlákno.

## <a name="syntax"></a>Syntaxe

```C
size_t _fwrite_nolock(
   const void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Ukazatel na data, která mají být zapsána.

*Velikost*<br/>
Položka velikost v bajtech.

*Počet*<br/>
Maximální počet položek, které mají být zapsána.

*Datový proud*<br/>
Ukazatel **souboru** struktura.

## <a name="return-value"></a>Návratová hodnota

Stejné jako [fwrite –](fwrite.md).

## <a name="remarks"></a>Poznámky

Tato funkce je verze bez uzamčení **fwrite –**. Je stejný jako **fwrite –** s tím rozdílem, že není chráněn před narušení další vlákna. Může být rychlejší, protože není nesnižuje režii uzamykání jiná vlákna. Tuto funkci můžete používejte pouze v kontextu vláken jako je například aplikace nebo kde oboru volání již zpracovává izolace přístup z více vláken.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fwrite_nolock**|\<stdio.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [fread –](fread.md).

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fread](fread.md)<br/>
[_write](write.md)<br/>
