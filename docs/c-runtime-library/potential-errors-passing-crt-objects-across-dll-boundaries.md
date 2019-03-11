---
title: Možné chyby při předávání objektů CRT přes hranice knihovny DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLL conflicts [C++]
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
ms.openlocfilehash: 31f9d9aceba167b516c9d37724e240f1bc4586e1
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749894"
---
# <a name="potential-errors-passing-crt-objects-across-dll-boundaries"></a>Možné chyby při předávání objektů CRT přes hranice knihovny DLL

Při předání C Run-time (CRT) objektů, jako jsou popisovače souborů, národní prostředí a proměnných prostředí do nebo z knihovny DLL (volání funkce přes hranice knihovny DLL), knihovny DLL, stejně jako soubory volání do knihovny DLL, použijte různé kopie může dojít k neočekávanému chování Knihovny CRT.

Související problém může vzniknout při přidělování paměti (buď explicitně pomocí `new` nebo `malloc`, nebo implicitně pomocí `strdup`, `strstreambuf::str`, a tak dále) a pak předejte ukazatel přes hranice knihovny DLL k uvolnění. To může způsobit poškození paměti přístup porušení nebo haldy, pokud knihovny DLL a její uživatelé používat různé kopie knihovny CRT.

Dalším symptomem tohoto problému může být chyba v okně Výstup během ladění, jako:

HEAP[]: Zadaná RtlValidateHeap(#,#) neplatná adresa

## <a name="causes"></a>Způsobí, že

Každá kopie knihovny CRT má samostatné a odlišné stavu, v místním úložišti vláken uchovává svou aplikaci nebo knihovny DLL. V důsledku toho CRT objektů, jako jsou popisovače souborů, proměnných prostředí a národní prostředí jsou platné pouze pro kopii CRT v aplikaci nebo knihovny DLL, ve kterém jsou tyto objekty přidělené nebo nastavit. Když knihovny DLL a svým klientům aplikace používají různé kopie knihovny CRT, nelze předat těchto objektů CRT přes hranice knihovny DLL a představ, aby ji mohla správně na druhé straně. To platí hlavně CRT verze starší než Universal CRT v sadě Visual Studio 2015 a novější. Došlo k specifické pro verzi knihovny CRT pro každou verzi sady Visual Studio vytvořené pomocí sady Visual C++ 2013 nebo starší. Podrobnosti interní implementace CRT, například její datové struktury a konvence pojmenování, se liší v jednotlivých verzích. Dynamické propojování kódu zkompilovaném pro jednu verzi CRT na jinou verzi knihovny DLL CRT se nikdy podporuje, ale čas od času ji by fungovalo, více podle štěstí než záměrné.

Protože každá kopie knihovny CRT má své vlastní správce hald, přidělení paměti v jedné knihovně CRT a předání ukazatele přes hranice knihovny DLL na uvolnění různé kopie knihovny CRT je také možná příčina pro poškození haldy. Při návrhu vaší knihovny DLL tak, aby ji předá objektů CRT přes hranice nebo přidělí paměť a očekává, že k uvolnění mimo knihovnu DLL, můžete omezit aplikace klienty knihovny DLL použít stejnou kopii knihovny CRT jako knihovnu DLL. Knihovny DLL a jeho klienty normálně používat stejnou kopii knihovny CRT pouze v případě, že jsou propojeny v okamžiku načtení na stejnou verzi CRT knihovny DLL. Protože DLL verze knihovny Universal CRT používané službou Visual Studio 2015 a novější na systému Windows 10 je teď komponenta Windows centrálně nasazené ucrtbase.dll, je stejný pro aplikace vytvořené pomocí sady Visual Studio 2015 a novější verze. Nicméně i v případě, že je stejný jako kód CRT, nelze předáte paměť přidělena v haldě jedné součásti, která používá různé haldy.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Tento příklad předává popisovač souboru přes hranice knihovny DLL.

Soubor knihovny DLL a .exe jsou vytvořeny tak, /, / MD, sdílejí jedinou kopii CRT.

Pokud je znovu sestavit pomocí/MT, tak, že používají oddělené kopie CRT, používané výsledný výsledky test1Main.exe narušení přístupu.

```cpp
// test1Dll.cpp
// compile with: cl /EHsc /W4 /MD /LD test1Dll.cpp
#include <stdio.h>
__declspec(dllexport) void writeFile(FILE *stream)
{
   char   s[] = "this is a string\n";
   fprintf( stream, "%s", s );
   fclose( stream );
}
```

```cpp
// test1Main.cpp
// compile with: cl /EHsc /W4 /MD test1Main.cpp test1Dll.lib
#include <stdio.h>
#include <process.h>
void writeFile(FILE *stream);

int main(void)
{
   FILE  * stream;
   errno_t err = fopen_s( &stream, "fprintf.out", "w" );
   writeFile(stream);
   system( "type fprintf.out" );
}
```

```Output
this is a string
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Tento příklad předává proměnné prostředí přes hranice knihovny DLL.

```cpp
// test2Dll.cpp
// compile with: cl /EHsc /W4 /MT /LD test2Dll.cpp
#include <stdio.h>
#include <stdlib.h>

__declspec(dllexport) void readEnv()
{
   char *libvar;
   size_t libvarsize;

   /* Get the value of the MYLIB environment variable. */
   _dupenv_s( &libvar, &libvarsize, "MYLIB" );

   if( libvar != NULL )
      printf( "New MYLIB variable is: %s\n", libvar);
   else
      printf( "MYLIB has not been set.\n");
   free( libvar );
}
```

```cpp
// test2Main.cpp
// compile with: cl /EHsc /W4 /MT test2Main.cpp test2dll.lib
#include <stdlib.h>
#include <stdio.h>

void readEnv();

int main( void )
{
   _putenv( "MYLIB=c:\\mylib;c:\\yourlib" );
   readEnv();
}
```

```Output
MYLIB has not been set.
```

Pokud soubor knihovny DLL a .exe jsou vytvořeny tak, / MD, tak, aby se používá jenom jednu kopii CRT, program úspěšně spuštěn a vytvoří následující výstup:

```
New MYLIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Viz také:

[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)
