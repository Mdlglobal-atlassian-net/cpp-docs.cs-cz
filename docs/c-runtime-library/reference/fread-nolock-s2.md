---
title: _fread_nolock_s2
ms.date: 11/04/2016
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
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
ms.openlocfilehash: 1dccbd362577e524f0455a2248d4d0f209ea6295
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580785"
---
# <a name="freadnolocks"></a>_fread_nolock_s

Čte data z datového proudu, bez blokování jiných vláken. Tato verze [fread_nolock –](fread-nolock.md) má rozšíření zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Maximální počet položek, které chcete načíst.

*Stream*<br/>
Ukazatel na **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

Zobrazit [fread_s](fread-s.md).

## <a name="remarks"></a>Poznámky

Tato funkce je nezamykací verzi **fread_s**. Je stejný jako **fread_s** s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Může být rychlejší, protože narůstání režii uzamykáním ostatních vláken. Tuto funkci lze používejte pouze v kontextech bezpečných na vlákna, jako je například aplikace s jedním vláknem nebo pokud volající obor již zpracovává izolaci vláken.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fread_nolock_s**|C: \<stdio.h >; Jazyk C++: \<cstdio – > nebo \<stdio.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
