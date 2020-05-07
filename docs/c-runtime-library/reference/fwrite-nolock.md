---
title: _fwrite_nolock
ms.date: 4/2/2020
api_name:
- _fwrite_nolock
- _o__fwrite_nolock
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fwrite_nolock
- fwrite_nolock
helpviewer_keywords:
- fwrite_nolock function
- streams, writing data to
- _fwrite_nolock function
ms.assetid: 2b4ec6ce-742e-4615-8407-44a0a18ec1d7
ms.openlocfilehash: 6856dd2af0536deacfbef6b02c7cdf38d41f9c04
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919436"
---
# <a name="_fwrite_nolock"></a>_fwrite_nolock

Zapisuje data do datového proudu bez uzamčení vlákna.

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

*vyrovnávací paměti*<br/>
Ukazatel na data, která mají být zapsána.

*hodnota*<br/>
Velikost položky v bajtech

*výpočtu*<br/>
Maximální počet položek, které mají být zapsány.

*Stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

Stejné jako [fwrite](fwrite.md).

## <a name="remarks"></a>Poznámky

Tato funkce je neuzamknutá verze **fwrite**. Je totožný s **fwrite** s tím rozdílem, že není chráněna před rušením jinými vlákny. Může být rychlejší, protože nevzniká režie na uzamykání jiných vláken. Tuto funkci použijte pouze v kontextech bezpečných pro přístup z více vláken, jako jsou například aplikace s jedním vláknem nebo kde volající obor již zpracovává izolaci vlákna.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fwrite_nolock**|\<stdio. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [fread](fread.md).

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fread](fread.md)<br/>
[_write](write.md)<br/>
