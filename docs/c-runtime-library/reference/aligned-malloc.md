---
title: _aligned_malloc
ms.date: 4/2/2020
api_name:
- _aligned_malloc
- _o__aligned_malloc
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
- _aligned_malloc
- alligned_malloc
helpviewer_keywords:
- aligned_malloc function
- _aligned_malloc function
ms.assetid: fb788d40-ee94-4039-aa4d-97d73dab1ca0
ms.openlocfilehash: b7d7f29f50b28ff713de94cc3304014e96d45b70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350607"
---
# <a name="_aligned_malloc"></a>_aligned_malloc

Přidělí paměť na zadanou hranici trasy.

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_malloc(
    size_t size,
    size_t alignment
);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Velikost požadované přidělení paměti.

*Zarovnání*<br/>
Hodnota zarovnání, která musí být celá mocnina 2.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na blok paměti, který byl přidělen nebo null, pokud se operace nezdařila. Ukazatel je násobkem *zarovnání*.

## <a name="remarks"></a>Poznámky

**_aligned_malloc** je založen na [malloc](malloc.md).

**_aligned_malloc** je `__declspec(noalias)` `__declspec(restrict)`označena a , což znamená, že je zaručeno, že funkce nebude měnit globální proměnné a že vrácený ukazatel není aliasován. Další informace naleznete v [tématu noalias](../../cpp/noalias.md) a [restrict](../../cpp/restrict.md).

Tato funkce `errno` `ENOMEM` nastaví, pokud se nezdařilo přidělení `_HEAP_MAXREQ`paměti nebo pokud požadovaná velikost byla větší než . Další informace `errno`o tématech [naleznete v tématech errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Také **_aligned_malloc** ověřuje jeho parametry. Pokud *trasování* není mocninu 2 nebo *velikost* je nula, tato funkce vyvolá neplatný obslužnou rutinu parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, vrátí `errno` tato `EINVAL`funkce hodnotu NULL a nastaví na .

Pomocí [_aligned_free](aligned-free.md) můžete navrátit paměť `_aligned_offset_malloc`získanou **_aligned_malloc** i . Nepoužívejte `free`, který nerekultivuje zarovnané paměti správně a může vést k těžko diagnostikovat chyby.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_malloc**|\<malloc.h>|

## <a name="example"></a>Příklad

```C
// crt_aligned_malloc.c

#include <malloc.h>
#include <stdio.h>

int main() {
    void    *ptr;
    size_t  alignment,
            off_set;

    // Note alignment should be 2^N where N is any positive int.
    alignment = 16;
    off_set = 5;

    // Using _aligned_malloc
    ptr = _aligned_malloc(100, alignment);
    if (ptr == NULL)
    {
        printf_s( "Error allocation aligned memory.");
        return -1;
    }
    if (((unsigned long long)ptr % alignment ) == 0)
        printf_s( "This pointer, %p, is aligned on %zu\n",
                  ptr, alignment);
    else
        printf_s( "This pointer, %p, is not aligned on %zu\n",
                  ptr, alignment);

    // Using _aligned_realloc
    ptr = _aligned_realloc(ptr, 200, alignment);
    if ( ((unsigned long long)ptr % alignment ) == 0)
        printf_s( "This pointer, %p, is aligned on %zu\n",
                  ptr, alignment);
    else
        printf_s( "This pointer, %p, is not aligned on %zu\n",
                  ptr, alignment);
    _aligned_free(ptr);

    // Using _aligned_offset_malloc
    ptr = _aligned_offset_malloc(200, alignment, off_set);
    if (ptr == NULL)
    {
        printf_s( "Error allocation aligned offset memory.");
        return -1;
    }
    if ( ( (((unsigned long long)ptr) + off_set) % alignment ) == 0)
        printf_s( "This pointer, %p, is offset by %zu on alignment of %zu\n",
                  ptr, off_set, alignment);
    else
        printf_s( "This pointer, %p, does not satisfy offset %zu "
                  "and alignment %zu\n",ptr, off_set, alignment);

    // Using _aligned_offset_realloc
    ptr = _aligned_offset_realloc(ptr, 200, alignment, off_set);
    if (ptr == NULL)
    {
        printf_s( "Error reallocation aligned offset memory.");
        return -1;
    }
    if ( ( (((unsigned long long)ptr) + off_set) % alignment ) == 0)
        printf_s( "This pointer, %p, is offset by %zu on alignment of %zu\n",
                  ptr, off_set, alignment);
    else
        printf_s( "This pointer, %p, does not satisfy offset %zu and "
                  "alignment %zu\n", ptr, off_set, alignment);

    // Note that _aligned_free works for both _aligned_malloc
    // and _aligned_offset_malloc. Using free is illegal.
    _aligned_free(ptr);
}
```

```Output
This pointer, 3280880, is aligned on 16
This pointer, 3280880, is aligned on 16
This pointer, 3280891, is offset by 5 on alignment of 16
This pointer, 3280891, is offset by 5 on alignment of 16
```

## <a name="see-also"></a>Viz také

[Zarovnání dat](../../c-runtime-library/data-alignment.md)
