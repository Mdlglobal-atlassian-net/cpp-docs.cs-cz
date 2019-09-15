---
title: _fread_nolock_s2
ms.date: 11/04/2016
api_name:
- _fread_nolock_s
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
- _fread_nolock_s
- stdio/_fread_nolock_s
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
ms.openlocfilehash: e7fded9860b7a1364841d5f9b8a7e3aa478a8420
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956892"
---
# <a name="_fread_nolock_s"></a>_fread_nolock_s

Načte data z datového proudu bez uzamknutí jiných vláken. Tato verze [fread_nolock](fread-nolock.md) má vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*vyrovnávací paměti*<br/>
Umístění úložiště pro data

*bufferSize*<br/>
Velikost cílové vyrovnávací paměti v bajtech

*elementSize*<br/>
Velikost položky, která se má načíst v bajtech

*Nedisponuje ElementCount*<br/>
Maximální počet položek, které se mají přečíst

*stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

Viz [fread_s](fread-s.md).

## <a name="remarks"></a>Poznámky

Tato funkce je neuzamknutá verze **fread_s**. Je totožný s **fread_s** s tím rozdílem, že není chráněna před rušením jinými vlákny. Může být rychlejší, protože nevzniká režie na uzamykání jiných vláken. Tuto funkci použijte pouze v kontextech bezpečných pro přístup z více vláken, jako jsou například aplikace s jedním vláknem nebo kde volající obor již zpracovává izolaci vlákna.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fread_nolock_s**|C: \<stdio. h >; C++ :\<cstdio > nebo \<stdio. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
