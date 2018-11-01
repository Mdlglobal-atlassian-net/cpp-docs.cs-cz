---
title: _aligned_offset_malloc
ms.date: 11/04/2016
apiname:
- _aligned_offset_malloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _aligned_offset_malloc
- aligned_offset_malloc
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
ms.openlocfilehash: 824edfd8bb96d805a030fb205dee62fa9eb4fd06
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644636"
---
# <a name="alignedoffsetmalloc"></a>_aligned_offset_malloc

Přidělí paměť v zadaných hranicích zarovnání.

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_offset_malloc(
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Velikost požadované alokace paměti.

*Zarovnání*<br/>
Hodnota zarovnání, které musí být celočíselnou mocninou 2.

*Posun*<br/>
Posun na přidělení paměti pro vynucení zarovnání.

## <a name="return-value"></a>Návratová hodnota

Ukazatele na blok paměti, která byla přidělena nebo **NULL** Pokud se operace nezdařila.

## <a name="remarks"></a>Poznámky

**_aligned_offset_malloc –** je užitečné v situacích, kde je potřeba zarovnání na prvek vnořené; například, pokud zarovnání bylo potřeba ve vnořené třídě.

**_aligned_offset_malloc –** vychází **malloc**; Další informace najdete v tématu [malloc](malloc.md).

**_aligned_offset_malloc –** je označen `__declspec(noalias)` a `__declspec(restrict)`, což znamená, že funkce je zaručeno, že neupraví globální proměnné a Vrácený ukazatel není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).

Tato funkce nastaví **errno** k **ENOMEM** Pokud přidělení paměti se nezdařilo nebo pokud byla větší než požadovaná velikost **_heap_maxreq –**. Další informace o **errno**, naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc **_aligned_offset_malloc –** ověří jeho parametry. Pokud *zarovnání* není mocninou čísla 2 nebo, pokud *posun* je větší než nebo rovna hodnotě *velikost* a nenulovou hodnotu, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrací **NULL** a nastaví **errno** k **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_offset_malloc**|\<malloc.h >|

## <a name="example"></a>Příklad

Další informace najdete v tématu [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Viz také:

[Zarovnání dat](../../c-runtime-library/data-alignment.md)<br/>
