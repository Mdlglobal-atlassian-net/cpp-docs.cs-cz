---
title: terminate (CRT)
ms.date: 4/2/2020
api_name:
- terminate
- _o_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- terminate
helpviewer_keywords:
- terminate function
- exception handling, termination
ms.assetid: 90e67402-08e9-4b2a-962c-66a8afd3ccb4
ms.openlocfilehash: 1aa95daeab424c933f10060fb4f87cb317aa188c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362545"
---
# <a name="terminate-crt"></a>terminate (CRT)

Volání [přerušení](abort.md) nebo funkce, kterou zadáte pomocí **set_terminate**.

## <a name="syntax"></a>Syntaxe

```C
void terminate( void );
```

## <a name="remarks"></a>Poznámky

Funkce **terminate** se používá při zpracování výjimek jazyka C++ a volá se v následujících případech:

- Odpovídající catch obslužná rutina nebyla nalezena pro vyzývací výjimku jazyka C++.

- Výjimka je vyvolána funkce destruktoru během unwind zásobníku.

- Zásobník je poškozen po vyvolání výjimky.

**ve** výchozím nastavení [přerušit přerušení](abort.md) volání. Toto výchozí nastavení můžete změnit zápisem vlastní funkce ukončení a voláním **set_terminate** s názvem funkce jako argumentem. **ukončit** volání poslední funkce uvedené jako argument **k set_terminate**. Další informace naleznete [v tématu Unhandled C++ Exceptions](../../cpp/unhandled-cpp-exceptions.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**Ukončit**|\<eh.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```cpp
// crt_terminate.cpp
// compile with: /EHsc
#include <eh.h>
#include <process.h>
#include <iostream>
using namespace std;

void term_func();

int main()
{
    int i = 10, j = 0, result;
    set_terminate( term_func );
    try
    {
        if( j == 0 )
            throw "Divide by zero!";
        else
            result = i/j;
    }
    catch( int )
    {
        cout << "Caught some integer exception.\n";
    }
    cout << "This should never print.\n";
}

void term_func()
{
    cout << "term_func() was called by terminate().\n";

    // ... cleanup tasks performed here

    // If this function does not exit, abort is called.

    exit(-1);
}
```

```Output
term_func() was called by terminate().
```

## <a name="see-also"></a>Viz také

[Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)<br/>
[Přerušení](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Neočekávané](unexpected-crt.md)<br/>
