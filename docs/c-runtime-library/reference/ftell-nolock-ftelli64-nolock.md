---
title: _ftell_nolock, _ftelli64_nolock
ms.date: 11/04/2016
api_name:
- _ftelli64_nolock
- _ftell_nolock
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
- _ftelli64_nolock
- ftelli64_nolock
- ftell_nolock
- _ftell_nolock
helpviewer_keywords:
- ftelli64_nolock function
- _ftelli64_nolock function
- _ftell_nolock function
- ftell_nolock function
- file pointers [C++], getting current position
ms.assetid: 84e68b0a-32f8-4c4a-90ad-3f2387685ede
ms.openlocfilehash: 9e72687077cc5401bb411fca81a3ccec48a6258f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956356"
---
# <a name="_ftell_nolock-_ftelli64_nolock"></a>_ftell_nolock, _ftelli64_nolock

Získá aktuální pozici ukazatele souboru bez uzamknutí vlákna.

## <a name="syntax"></a>Syntaxe

```C
long _ftell_nolock(
   FILE *stream
);
__int64 _ftelli64_nolock(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Zaměřte se na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

Stejné jako **ftell** a **_ftelli64**. Další informace najdete v tématu [ftell, _ftelli64](ftell-ftelli64.md).

## <a name="remarks"></a>Poznámky

Tyto funkce jsou neuzamykání verzí **ftell** a **_ftelli64**v uvedeném pořadí. Jsou stejné jako **ftell** a **_ftelli64** s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Tyto funkce mohou být rychlejší, protože neúčtují režii na uzamykání jiných vláken. Tyto funkce použijte pouze v kontextech bezpečných pro přístup z více vláken, jako jsou například aplikace s jedním vláknem nebo kde volající obor již zpracovává izolaci vlákna.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|--------------|---------------------|---------------------|
|**ftell_nolock**|\<stdio.h>|\<errno.h>|
|**_ftelli64_nolock**|\<stdio.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
