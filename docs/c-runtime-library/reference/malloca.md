---
title: _malloca
ms.date: 11/04/2016
api_name:
- _malloca
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
- malloca
- _malloca
helpviewer_keywords:
- memory allocation, stack
- malloca function
- _malloca function
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
ms.openlocfilehash: 0b12b4adde710f2fc46b3a3790519006fabbb1fc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952778"
---
# <a name="_malloca"></a>_malloca

Přidělí paměť v zásobníku. Jedná se o verzi [_alloca](alloca.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
void *_malloca(
   size_t size
);
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Bajtů, které se mají přidělit ze zásobníku.

## <a name="return-value"></a>Návratová hodnota

Rutina **_malloca** vrací ukazatel **void** do přiděleného místa, což je zaručeno, že bude vhodně zarovnána pro uložení libovolného typu objektu. Pokud je *Velikost* 0, **_malloca** přiděluje položku s nulovou délkou a vrátí platný ukazatel na tuto položku.

Pokud je *Velikost* větší než **_ALLOCA_S_THRESHOLD**, pak se **_malloca** pokusí přidělit na haldu a vrátí ukazatel s hodnotou null, pokud nelze prostor přidělit. Pokud je *Velikost* menší nebo rovna **_ALLOCA_S_THRESHOLD**, pak se **_malloca** pokusí přidělit v zásobníku a výjimka přetečení zásobníku je vygenerována, pokud nelze prostor přidělit. Výjimka přetečení zásobníku není C++ výjimkou. Jedná se o strukturovanou výjimku. Namísto použití C++ zpracování výjimek je třeba pro zachycení této výjimky použít [strukturované zpracování výjimek](../../cpp/structured-exception-handling-c-cpp.md) (SEH).

## <a name="remarks"></a>Poznámky

**_malloca** přiděluje bajty *velikosti* ze zásobníku programu nebo haldy, pokud požadavek překročí určitou velikost v bajtech vydaných pomocí **_ALLOCA_S_THRESHOLD**. Rozdíl mezi **_malloca** a **_alloca** je, že **_alloca** vždy přiděluje v zásobníku bez ohledu na velikost. Na rozdíl od **_alloca**, která nevyžaduje nebo nepovoluje volání **, aby uvolnilo** paměť, která je tak přidělena, **_malloca** vyžaduje použití [_freea](freea.md) k uvolnění paměti. V režimu ladění **_malloca** vždy přiděluje paměť z haldy.

Existují omezení pro explicitní volání **_malloca** v obslužné rutině výjimky (eh). Rutiny EH, které běží na procesorech x86, fungují ve vlastním zásobníku paměti: Provádějí své úkoly v paměťovém prostoru, který není založen na aktuálním umístění ukazatele zásobníku ohraničující funkce. Mezi nejběžnější implementace patří strukturované zpracování výjimek systému Windows NT (SEH) a C++ výrazy klauzule catch. Proto explicitní volání **_malloca** v některém z následujících scénářů způsobí selhání programu při návratu do rutiny Calling eh:

- Výraz filtru výjimky SEH Windows NT: **__except** (`_malloca ()` )

- Koncová obslužná rutina výjimky Windows NT SEH`_malloca ()` : __finally {}

- C++Výraz klauzule catch pro EH

**_Malloca** lze však volat přímo z rutiny EH nebo z zpětného volání dodaného aplikací, které je vyvoláno jedním z výše uvedených scénářů eh.

> [!IMPORTANT]
> Pokud je v systému Windows XP volána **_malloca** uvnitř bloku try/catch, je nutné volat [_resetstkoflw](resetstkoflw.md) v bloku catch.

Kromě výše uvedených omezení při použití možnosti [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) nelze použít **_malloca** v blocích **__except** . Další informace naleznete v tématu [omezení/CLR](../../build/reference/clr-restrictions.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_malloca**|\<. h >|

## <a name="example"></a>Příklad

```C
// crt_malloca_simple.c
#include <stdio.h>
#include <malloc.h>

void Fn()
{
   char * buf = (char *)_malloca( 100 );
   // do something with buf
   _freea( buf );
}

int main()
{
   Fn();
}
```

## <a name="example"></a>Příklad

```C
// crt_malloca_exception.c
// This program demonstrates the use of
// _malloca and trapping any exceptions
// that may occur.

#include <windows.h>
#include <stdio.h>
#include <malloc.h>

int main()
{
    int     size;
    int     numberRead = 0;
    int     errcode = 0;
    void    *p = NULL;
    void    *pMarker = NULL;

    while (numberRead == 0)
    {
        printf_s("Enter the number of bytes to allocate "
                 "using _malloca: ");
        numberRead = scanf_s("%d", &size);
    }

    // Do not use try/catch for _malloca,
    // use __try/__except, since _malloca throws
    // Structured Exceptions, not C++ exceptions.

    __try
    {
        if (size > 0)
        {
            p =  _malloca( size );
        }
        else
        {
            printf_s("Size must be a positive number.");
        }
        _freea( p );
    }

    // Catch any exceptions that may occur.
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )
    {
        printf_s("_malloca failed!\n");

        // If the stack overflows, use this function to restore.
        errcode = _resetstkoflw();
        if (errcode)
        {
            printf("Could not reset the stack!");
            _exit(1);
        }
    };
}
```

### <a name="input"></a>Vstup

```Input
1000
```

### <a name="sample-output"></a>Vzorový výstup

```Output
Enter the number of bytes to allocate using _malloca: 1000
```

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
