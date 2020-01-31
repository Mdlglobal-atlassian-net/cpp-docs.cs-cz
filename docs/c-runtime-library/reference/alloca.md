---
title: _alloca
ms.date: 11/04/2016
api_name:
- _alloca
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _alloca
- alloca
helpviewer_keywords:
- memory allocation, stack
- alloca function
- _alloca function
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
ms.openlocfilehash: 77ce6e0cdb5e1ad3f5317989c7804abc5aed4e69
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821431"
---
# <a name="_alloca"></a>_alloca

Přidělí paměť v zásobníku. Tato funkce je zastaralá, protože je k dispozici bezpečnější verze; viz [_malloca](malloca.md).

## <a name="syntax"></a>Syntaxe

```C
void *_alloca(
   size_t size
);
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Bajtů, které se mají přidělit ze zásobníku.

## <a name="return-value"></a>Návratová hodnota

Rutina **_alloca** vrací **anulování** ukazatele na přidělené místo, což je zaručeno, že bude vhodně zarovnán pro uložení libovolného typu objektu. Pokud je *Velikost* 0, **_alloca** přiděluje položku nulové délky a vrátí platný ukazatel na tuto položku.

Výjimka přetečení zásobníku je vygenerována, pokud nelze prostor přidělit. Výjimka přetečení zásobníku není C++ výjimkou. Jedná se o strukturovanou výjimku. Namísto použití C++ zpracování výjimek je nutné použít [strukturované zpracování výjimek](../../cpp/structured-exception-handling-c-cpp.md) (SEH).

## <a name="remarks"></a>Poznámky

**_alloca** přiděluje bajty *velikosti* ze zásobníku programu. Přidělené místo je automaticky uvolněno při ukončení volání funkce (ne v případě, že přidělení se pouze předává mimo rozsah). Proto nepředávejte hodnotu ukazatele vrácenou **_alloca** jako argument pro [uvolnění](free.md).

Existují omezení pro explicitní volání **_alloca** v obslužné rutině výjimky (eh). Rutiny EH, které běží na procesorech x86, fungují ve vlastním paměťovém snímku: provádějí své úkoly v paměťovém prostoru, který není založen na aktuálním umístění ukazatele zásobníku nadřazené funkce. Mezi nejběžnější implementace patří strukturované zpracování výjimek systému Windows NT (SEH) a C++ výrazy klauzule catch. Proto explicitní volání **_alloca** v některém z následujících scénářů způsobí selhání programu při návratu do rutiny Calling eh:

- Výraz filtru výjimky SEH Windows NT: `__except ( _alloca() )`

- Koncová obslužná rutina výjimky Windows NT SEH: `__finally { _alloca() }`

- C++Výraz klauzule catch pro EH

**_Alloca** lze však volat přímo z rutiny EH nebo z zpětného volání dodaného aplikací, které je vyvoláno jedním z výše uvedených scénářů eh.

> [!IMPORTANT]
> Pokud je v systému Windows XP volána **_alloca** uvnitř bloku try/catch, je nutné volat [_resetstkoflw](resetstkoflw.md) v bloku catch.

Kromě výše uvedených omezení při použití možnosti[/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) **_alloca** nelze použít v blocích **__except** . Další informace naleznete v tématu [omezení/CLR](../../build/reference/clr-restrictions.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_alloca**|\<. h >|

## <a name="example"></a>Příklad

```C
// crt_alloca.c
// This program demonstrates the use of
// _alloca and trapping any exceptions
// that may occur.

#include <windows.h>
#include <stdio.h>
#include <malloc.h>

int main()
{
    int     size = 1000;
    int     errcode = 0;
    void    *pData = NULL;

    // Note: Do not use try/catch for _alloca,
    // use __try/__except, since _alloca throws
    // Structured Exceptions, not C++ exceptions.

    __try {
        // An unbounded _alloca can easily result in a
        // stack overflow.
        // Checking for a size < 1024 bytes is recommended.
        if (size > 0 && size < 1024)
        {
            pData = _alloca( size );
            printf_s( "Allocated %d bytes of stack at 0x%p",
                      size, pData);
        }
        else
        {
            printf_s("Tried to allocate too many bytes.\n");
        }
    }

    // If an exception occurred with the _alloca function
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )
    {
        printf_s("_alloca failed!\n");

        // If the stack overflows, use this function to restore.
        errcode = _resetstkoflw();
        if (errcode)
        {
            printf_s("Could not reset the stack!\n");
            _exit(1);
        }
    };
}
```

```Output
Allocated 1000 bytes of stack at 0x0012FB50
```

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
[_malloca](malloca.md)<br/>
