---
title: _alloca
ms.date: 11/04/2016
apiname:
- _alloca
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
apitype: DLLExport
f1_keywords:
- _alloca
- alloca
helpviewer_keywords:
- memory allocation, stack
- alloca function
- _alloca function
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
ms.openlocfilehash: 7c083e791301d3224709a5fc6c711ceaa6397d38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668068"
---
# <a name="alloca"></a>_alloca

Přidělí paměť v zásobníku. Tato funkce je zastaralá, protože bezpečnější verze je k dispozici. Zobrazit [_malloca](malloca.md).

## <a name="syntax"></a>Syntaxe

```C
void *_alloca(
   size_t size
);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Bajtů, které mají být přiděleny ze zásobníku.

## <a name="return-value"></a>Návratová hodnota

**_Alloca** rutinní vrátí **void** ukazatel do přiděleného místa, což je zaručeno, že jako vhodně zarovnaný pro úložiště libovolného typu objektu. Pokud *velikost* je 0, **_alloca** přiděluje položku nulové délky a vrátí platný ukazatel na danou položku.

Pokud nelze přidělit místo, vygeneruje se k výjimce přetečení zásobníku. Výjimku přetečení zásobníku není výjimky jazyka C++; je strukturovaných výjimek. Místo používání zpracování výjimek jazyka C++, je nutné použít [strukturovaného zpracování výjimek](../../cpp/structured-exception-handling-c-cpp.md) (SEH).

## <a name="remarks"></a>Poznámky

**_alloca** přiděluje *velikost* bajtů ze zásobníku programu. Do přiděleného místa je automaticky uvolněn při ukončení volání funkce (ne už při přidělení předává pouze mimo rozsah). Proto, nepředávejte hodnotu ukazatele vrácené **_alloca** jako argument [bezplatné](free.md).

Existují omezení explicitně voláním **_alloca** v obslužné rutiny výjimek (EH). Rutiny EH, na kterých běží na procesorech x86 třídy pracovat v rámci své vlastní paměti: provádějí své úkoly v paměti, který není založen na aktuální umístění ukazatel zásobníku nadřazené funkce. Většina běžných implementací zahrnují zpracování (SEH) systému Windows NT strukturovaných výjimek a výrazy klauzule catch C++. Proto se explicitně voláním **_alloca** v některém z následujících výsledků scénáře selhání programu při vrácení volání rutiny EH:

- Výraz filtru výjimky SEH Windows NT: `__except ( _alloca() )`

- Windows NT SEH poslední obslužnou rutinu: `__finally { _alloca() }`

- Výraz klauzule catch C++ EH

Ale **_alloca** mohou být volány přímo z v rámci rutiny EH nebo ze zpětného volání s poskytované aplikací, která získá vyvolá jednu z výše uvedených scénářů EH.

> [!IMPORTANT]
> Ve Windows XP Pokud **_alloca** je volána uvnitř bloku try/catch, je nutné volat [_resetstkoflw](resetstkoflw.md) v bloku catch.

Kromě výše uvedená omezení při použití[/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) možnost **_alloca** nelze použít v **__except** bloky. Další informace najdete v tématu [/CLR – omezení](../../build/reference/clr-restrictions.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_alloca**|\<malloc.h >|

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

    // If an exception occured with the _alloca function
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
