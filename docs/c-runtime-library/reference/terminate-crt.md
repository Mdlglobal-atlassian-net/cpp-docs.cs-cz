---
title: terminate (CRT)
ms.date: 11/04/2016
api_name:
- terminate
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
ms.openlocfilehash: b76ce42817fa1a6b79ef32965fcfa550a508e88d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946202"
---
# <a name="terminate-crt"></a>terminate (CRT)

Volání funkce [Abort](abort.md) nebo funkce, kterou zadáte, pomocí **set_terminate**.

## <a name="syntax"></a>Syntaxe

```C
void terminate( void );
```

## <a name="remarks"></a>Poznámky

Funkce **ukončení** se používá s C++ zpracováním výjimek a je volána v následujících případech:

- Pro vyvolanou C++ výjimku nejde najít vyhovující obslužnou rutinu catch.

- Výjimka je vyvolána funkcí destruktoru během unwind zásobníku.

- Zásobník je poškozen po vyvolání výjimky.

**ukončení** volání ve výchozím nastavení [přerušeno](abort.md) . Toto výchozí nastavení můžete změnit vytvořením vlastní ukončovací funkce a voláním **set_terminate** s názvem vaší funkce jako argumentem. **ukončení** volá poslední funkci zadanou jako argument pro **set_terminate**. Další informace naleznete v tématu [neošetřené C++ výjimky](../../cpp/unhandled-cpp-exceptions.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ruší**|\<eh.h>|

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

## <a name="see-also"></a>Viz také:

[Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
