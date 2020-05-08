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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 1ec4e27096dd6b5fea089e21c95022542d7adc82
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912214"
---
# <a name="terminate-crt"></a>terminate (CRT)

Volání funkce [Abort](abort.md) nebo funkce, kterou zadáte, pomocí **set_terminate**.

## <a name="syntax"></a>Syntaxe

```C
void terminate( void );
```

## <a name="remarks"></a>Poznámky

Funkce **ukončení** se používá při zpracování výjimek jazyka C++ a je volána v následujících případech:

- Pro vyvolanou výjimku jazyka C++ nelze nalézt vyhovující obslužnou rutinu catch.

- Výjimka je vyvolána funkcí destruktoru během unwind zásobníku.

- Zásobník je poškozen po vyvolání výjimky.

**ukončení** volání ve výchozím nastavení [přerušeno](abort.md) . Toto výchozí nastavení můžete změnit vytvořením vlastní ukončovací funkce a voláním **set_terminate** s názvem vaší funkce jako argumentem. **ukončení** volá poslední funkci zadanou jako argument pro **set_terminate**. Další informace naleznete v tématu [neošetřené výjimky jazyka C++](../../cpp/unhandled-cpp-exceptions.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ruší**|\<Eh. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
[přerušit](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[neočekávané](unexpected-crt.md)<br/>
