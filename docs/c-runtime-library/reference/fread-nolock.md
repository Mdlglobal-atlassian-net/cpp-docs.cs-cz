---
title: _fread_nolock
ms.date: 11/04/2016
apiname:
- _fread_nolock
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
- _fread_nolock
- fread_nolock
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- fread_nolock function
- _fread_nolock function
- streams [C++], reading data from
ms.assetid: 60e4958b-1097-46f5-a77b-94af5e7dba40
ms.openlocfilehash: 81827363d670c7cdeeddcb86390323bf431c6f98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287912"
---
# <a name="freadnolock"></a>_fread_nolock

Čte data z datového proudu, bez blokování jiných vláken.

## <a name="syntax"></a>Syntaxe

```C
size_t _fread_nolock(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Umístění úložiště pro data.

*Velikost*<br/>
Velikost položky v bajtech.

*Počet*<br/>
Maximální počet položek, které chcete načíst.

*stream*<br/>
Ukazatel **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

Zobrazit [fread –](fread.md).

## <a name="remarks"></a>Poznámky

Tato funkce je nezamykací verzi **fread –**. Je stejný jako **fread –** s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Může být rychlejší, protože narůstání režii uzamykáním ostatních vláken. Tuto funkci lze používejte pouze v kontextech bezpečných na vlákna, jako je například aplikace s jedním vláknem nebo pokud volající obor již zpracovává izolaci vláken.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fread_nolock**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
