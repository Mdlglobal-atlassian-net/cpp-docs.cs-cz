---
title: _fread_nolock_s2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _fread_nolock_s
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
- _fread_nolock_s
- stdio/_fread_nolock_s
dev_langs:
- C++
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 55259cabf4edcbda53845d5b041bc05f4e792bc7
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="freadnolocks"></a>_fread_nolock_s

Čte data z datového proudu, bez blokování jiná vlákna. Tato verze [fread_nolock –](fread-nolock.md) má rozšířené zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
size_t _fread_nolock_s(
   void *buffer,
   size_t bufferSize,
   size_t elementSize,
   size_t elementCount,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Umístění úložiště pro data.

*BufferSize*<br/>
Velikost cílové vyrovnávací paměti v bajtech.

*elementSize*<br/>
Velikost položky ke čtení v bajtech.

*počtem elementCount*<br/>
Maximální počet položek ke čtení.

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

## <a name="return-value"></a>Návratová hodnota

V tématu [fread_s](fread-s.md).

## <a name="remarks"></a>Poznámky

Tato funkce je verze bez uzamčení **fread_s**. Je stejný jako **fread_s** s tím rozdílem, že není chráněn před narušení další vlákna. Může být rychlejší, protože není nesnižuje režii uzamykání jiná vlákna. Tuto funkci můžete používejte pouze v kontextu vláken jako je například aplikace nebo kde oboru volání již zpracovává izolace přístup z více vláken.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fread_nolock_s**|C: \<stdio.h >; C++: \<cstdio – > nebo \<stdio.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
