---
title: _aligned_offset_malloc
ms.date: 11/04/2016
api_name:
- _aligned_offset_malloc
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_offset_malloc
- aligned_offset_malloc
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
ms.openlocfilehash: 3e8d6f839f3c675b7543ff14f3f633b0c7d5151f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943861"
---
# <a name="_aligned_offset_malloc"></a>_aligned_offset_malloc

Přidělí paměť na zadané hranici zarovnání.

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_offset_malloc(
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Velikost požadované alokace paměti

*bod*<br/>
Hodnota zarovnání, která musí být celočíselnou mocninou 2.

*polohy*<br/>
Posun k přidělení paměti pro vynucení zarovnání.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na blok paměti, který byl přidělen nebo **null** v případě, že operace se nezdařila.

## <a name="remarks"></a>Poznámky

**_aligned_offset_malloc** je užitečné v situacích, kdy je nutné zarovnat na vnořeném prvku. Například pokud bylo zarovnání nutné pro vnořenou třídu.

_aligned_offset_malloc je založen na **za** . Další informace najdete [v tématu.](malloc.md)

**_aligned_offset_malloc** je označena `__declspec(restrict)`jako `__declspec(noalias)` , což znamená, že funkce zaručuje, že nemění globální proměnné a že ukazatel, který vrátil, nemá alias. Další informace najdete [v tématech a](../../cpp/noalias.md) [omezení](../../cpp/restrict.md).

Tato funkce nastaví **errno** na **ENOMEM** , pokud se přidělení paměti nepovedlo nebo pokud je požadovaná velikost větší než **_HEAP_MAXREQ**. Další informace o **errno**najdete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). **_Aligned_offset_malloc** také ověří své parametry. Pokud *Zarovnání* není mocninou 2 nebo pokud je *posun* větší nebo roven *velikosti* a nenulové hodnotě, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrátí **hodnotu null** a nastaví **errno** na **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_offset_malloc**|\<. h >|

## <a name="example"></a>Příklad

Další informace najdete v tématu [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Viz také:

[Zarovnání dat](../../c-runtime-library/data-alignment.md)<br/>
