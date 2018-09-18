---
title: _aligned_malloc | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_malloc
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
- _aligned_malloc
- alligned_malloc
dev_langs:
- C++
helpviewer_keywords:
- aligned_malloc function
- _aligned_malloc function
ms.assetid: fb788d40-ee94-4039-aa4d-97d73dab1ca0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b500471a3580af9045f1c42707a543669da48c7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063174"
---
# <a name="alignedmalloc"></a>_aligned_malloc

Přidělí paměť v zadaných hranicích zarovnání.

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_malloc(
    size_t size,
    size_t alignment
);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Velikost požadované alokace paměti.

*Zarovnání*<br/>
Hodnota zarovnání, které musí být celočíselnou mocninou 2.

## <a name="return-value"></a>Návratová hodnota

Ukazatele na blok paměti, která byla přidělena nebo hodnota NULL, pokud operace se nezdařila. Ukazatel je násobkem *zarovnání*.

## <a name="remarks"></a>Poznámky

**_aligned_malloc** vychází [malloc](malloc.md).

**_aligned_malloc** je označen `__declspec(noalias)` a `__declspec(restrict)`, což znamená, že funkce je zaručeno, že neupraví globální proměnné a Vrácený ukazatel není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).

Tato funkce nastaví `errno` k `ENOMEM` Pokud přidělení paměti se nezdařilo nebo pokud byla větší než požadovaná velikost `_HEAP_MAXREQ`. Další informace o `errno`, naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc **_aligned_malloc** ověří jeho parametry. Pokud *zarovnání* není mocninou čísla 2 nebo *velikost* je nula, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce vrátí hodnotu NULL a nastaví `errno` k `EINVAL`.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_malloc**|\<malloc.h >|

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

## <a name="see-also"></a>Viz také:

[Zarovnání dat](../../c-runtime-library/data-alignment.md)