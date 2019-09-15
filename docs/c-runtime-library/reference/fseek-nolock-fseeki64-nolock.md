---
title: _fseek_nolock, _fseeki64_nolock
ms.date: 11/04/2016
api_name:
- _fseek_nolock
- _fseeki64_nolock
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
- _fseek_nolock
- _fseeki64_nolock
- fseek_nolock
- fseeki64_nolock
helpviewer_keywords:
- _fseek_nolock function
- fseeki64_nolock function
- file pointers [C++], moving
- fseek_nolock function
- _fseeki64_nolock function
- seek file pointers
ms.assetid: 2dd4022e-b715-462b-b935-837561605a02
ms.openlocfilehash: c72f44b214893a6702f5da5594db7725a2f02136
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956528"
---
# <a name="_fseek_nolock-_fseeki64_nolock"></a>_fseek_nolock, _fseeki64_nolock

Přesune ukazatel na soubor do zadaného umístění.

## <a name="syntax"></a>Syntaxe

```C
int _fseek_nolock(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64_nolock(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Ukazatel na strukturu **souborů** .

*polohy*<br/>
Počet bajtů od *počátku*

*zdroji*<br/>
Počáteční pozice.

## <a name="return-value"></a>Návratová hodnota

Stejné jako [fseek](fseek-fseeki64.md) a [_fseeki64](fseek-fseeki64.md), v uvedeném pořadí.

## <a name="remarks"></a>Poznámky

Tyto funkce jsou neuzamykání verzí [fseek](fseek-fseeki64.md) a [_fseeki64](fseek-fseeki64.md)v uvedeném pořadí. Jedná se o shodné s [fseek](fseek-fseeki64.md) a [_fseeki64](fseek-fseeki64.md) s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Tyto funkce mohou být rychlejší, protože neúčtují režii na uzamykání jiných vláken. Tyto funkce použijte pouze v kontextech bezpečných pro přístup z více vláken, jako jsou například aplikace s jedním vláknem nebo kde volající obor již zpracovává izolaci vlákna.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fseek_nolock**, **_fseeki64_nolock**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
