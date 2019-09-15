---
title: _fwrite_nolock
ms.date: 11/04/2016
api_name:
- _fwrite_nolock
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
ms.openlocfilehash: 035ee1d958c6ea6a13481d92311733ded9ed5f2c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956207"
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

*stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

Stejné jako [fwrite](fwrite.md).

## <a name="remarks"></a>Poznámky

Tato funkce je neuzamknutá verze **fwrite**. Je totožný s **fwrite** s tím rozdílem, že není chráněna před rušením jinými vlákny. Může být rychlejší, protože nevzniká režie na uzamykání jiných vláken. Tuto funkci použijte pouze v kontextech bezpečných pro přístup z více vláken, jako jsou například aplikace s jedním vláknem nebo kde volající obor již zpracovává izolaci vlákna.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fwrite_nolock**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [fread](fread.md).

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fread](fread.md)<br/>
[_write](write.md)<br/>
