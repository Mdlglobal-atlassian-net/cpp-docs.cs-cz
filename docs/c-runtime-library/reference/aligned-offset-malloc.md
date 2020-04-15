---
title: _aligned_offset_malloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_malloc
- _o__aligned_offset_malloc
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 1f13afbab75d2926d1c642c1430a3ffe5ecbac8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350581"
---
# <a name="_aligned_offset_malloc"></a>_aligned_offset_malloc

Přidělí paměť na zadanou hranici trasy.

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
Velikost požadované přidělení paměti.

*Zarovnání*<br/>
Hodnota zarovnání, která musí být celá mocnina 2.

*Posun*<br/>
Posun do přidělení paměti vynutit zarovnání.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na blok paměti, který byl přidělen nebo **null,** pokud se operace nezdařila.

## <a name="remarks"></a>Poznámky

**_aligned_offset_malloc** je užitečné v situacích, kdy je potřeba zarovnání na vnořený prvek; například pokud zarovnání bylo potřeba na vnořené třídy.

**_aligned_offset_malloc** je založen na **malloc**; další informace naleznete v [tématu malloc](malloc.md).

**_aligned_offset_malloc** je `__declspec(noalias)` `__declspec(restrict)`označena a , což znamená, že je zaručeno, že funkce nebude měnit globální proměnné a že vrácený ukazatel není aliasován. Další informace naleznete v [tématu noalias](../../cpp/noalias.md) a [restrict](../../cpp/restrict.md).

Tato funkce nastaví **errno** na **ENOMEM,** pokud se přidělení paměti nezdařilo nebo pokud byla požadovaná velikost větší než **_HEAP_MAXREQ**. Další informace o **errno**naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Také **_aligned_offset_malloc** ověřuje jeho parametry. Pokud *trasování* není mocninu 2 nebo pokud *je posun* větší nebo roven *velikosti* a nenulová, tato funkce vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, vrátí tato funkce **hodnotu NULL** a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_offset_malloc**|\<malloc.h>|

## <a name="example"></a>Příklad

Další informace naleznete [v tématu _aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Viz také

[Zarovnání dat](../../c-runtime-library/data-alignment.md)<br/>
