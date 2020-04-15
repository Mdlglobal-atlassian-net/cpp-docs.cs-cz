---
title: _fread_nolock_s2
ms.date: 4/2/2020
api_name:
- _fread_nolock_s
- _o__fread_nolock_s
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
- _fread_nolock_s
- stdio/_fread_nolock_s
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
ms.openlocfilehash: 3fb34a75a0281058a1d70ce41e1ce33b4b1bbb59
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346138"
---
# <a name="_fread_nolock_s"></a>_fread_nolock_s

Čte data z datového proudu, bez uzamčení jiných vláken. Tato verze [fread_nolock](fread-nolock.md) obsahuje vylepšení zabezpečení, jak je popsáno v části [Funkce zabezpečení v crt](../../c-runtime-library/security-features-in-the-crt.md).

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

*Buffersize*<br/>
Velikost cílové vyrovnávací paměti v bajtech.

*elementVelikost*<br/>
Velikost položky číst v bajtů.

*elementCount*<br/>
Maximální počet položek ke čtení.

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

## <a name="return-value"></a>Návratová hodnota

Viz [fread_s](fread-s.md).

## <a name="remarks"></a>Poznámky

Tato funkce je neblokovací verze **fread_s**. Je totožný s **fread_s** kromě toho, že není chráněn před rušením jinými vlákny. Může být rychlejší, protože nevzniká režie uzamčení jiných vláken. Tuto funkci používejte pouze v kontextech bezpečných pro přístup z více vláken, jako jsou aplikace s jedním vláknem nebo kde rozsah volání již zpracovává izolaci vlákna.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fread_nolock_s**|C: \<stdio.h>; C++: \<cstdio \<> nebo stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
