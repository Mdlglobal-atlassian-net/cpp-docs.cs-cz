---
title: C++ukončení programu
description: Popisuje způsoby, jak exit C++program jazyka.
ms.date: 01/15/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
no-loc:
- exit
- abort
- return
- main
- atexit
- void
ms.openlocfilehash: f83c9d5da5b0a1127603a97fd7946e9cca43a7a5
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123952"
---
# <a name="c-program-termination"></a>C++ukončení programu

V C++nástroji můžete exit program tímto způsobem:

- Zavolejte funkci [exit](exit-function.md) .
- Zavolejte funkci [abort](abort-function.md) .
- Spustí příkaz [return](return-statement-cpp.md) z `main`.

## <a name="opno-locexit-function"></a>exit funkce

Funkce [exit](../c-runtime-library/reference/exit-exit-exit.md) deklarovaná v \<Stdlib. h > ukončí C++ program. Hodnota zadaná jako argument pro `exit` se vrátí do operačního systému jako kód return programu nebo kód exit. Podle konvence return kód nula znamená, že program byl úspěšně dokončen. Můžete použít konstanty EXIT_FAILURE a EXIT_SUCCESS, definované v \<Stdlib. h > k indikaci úspěchu nebo neúspěchu programu.

Vydání příkazu **return** z funkce `main` je ekvivalentní volání funkce `exit` s hodnotou return jako argumentu.

## <a name="opno-locabort-function"></a>abort funkce

Funkce [abort](../c-runtime-library/reference/abort.md) , která je deklarována také ve standardním souboru include \<Stdlib. h >, ukončí C++ program. Rozdíl mezi `exit` a `abort` je, že `exit` umožňuje provedení C++ zpracování ukončení za běhu (budou volány globální destruktory objektů), zatímco `abort` program ukončí hned. Funkce `abort` obchází normální proces zničení u inicializovaných globálních statických objektů. Obchází také jakékoli speciální zpracování, které bylo zadáno pomocí funkce [atexit](../c-runtime-library/reference/atexit.md) .

## <a name="opno-locatexit-function"></a>atexit funkce

Pomocí funkce [atexit](../c-runtime-library/reference/atexit.md) můžete určit akce, které se spustí před ukončením programu. Před spuštěním funkce zpracování exitnejsou inicializovány žádné globální statické objekty před voláním **atexit** .

## <a name="opno-locreturn-statement-in-opno-locmain"></a>příkaz return v main

Vydání příkazu [return](return-statement-cpp.md) z `main` je funkčně ekvivalentní pro volání funkce `exit`. Vezměte v úvahu v následujícím příkladu:

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

Příkazy `exit` a **return** v předchozím příkladu jsou funkčně identické. Nicméně C++ vyžaduje, aby funkce, které mají return jiné typy než **void** return hodnotu. Příkaz **return** umožňuje return hodnotu z `main`.

## <a name="destruction-of-static-objects"></a>Zničení statických objektů

Když zavoláte `exit` nebo spustíte příkaz **return** z `main`, statické objekty jsou zničeny v obráceném pořadí jejich inicializace (po volání `atexit`, pokud existuje). Následující příklad ukazuje, jak taková inicializace a vyčištění funguje.

### <a name="example"></a>Příklad

V následujícím příkladu jsou objekty static `sd1` a `sd2` vytvořeny a inicializovány před vstupem do `main`. Po ukončení tohoto programu pomocí příkazu **return** je nejprve zničena `sd2` a poté `sd1`. Destruktor třídy `ShowData` zavře soubory přidružené k těmto statickým objektům.

```cpp
// using_exit_or_return1.cpp
#include <stdio.h>
class ShowData {
public:
   // Constructor opens a file.
   ShowData( const char *szDev ) {
   errno_t err;
      err = fopen_s(&OutputDev, szDev, "w" );
   }

   // Destructor closes the file.
   ~ShowData() { fclose( OutputDev ); }

   // Disp function shows a string on the output device.
   void Disp( char *szData ) {
      fputs( szData, OutputDev );
   }
private:
   FILE *OutputDev;
};

//  Define a static object of type ShowData. The output device
//   selected is "CON" -- the standard output device.
ShowData sd1 = "CON";

//  Define another static object of type ShowData. The output
//   is directed to a file called "HELLO.DAT"
ShowData sd2 = "hello.dat";

int main() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

Jiný způsob psaní tohoto kódu je deklarace objektů `ShowData` s rozsahem bloku, čímž je umožněno jejich zničení, dostanou-li se mimo rozsah:

```cpp
int main() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>Viz také:

[main funkce a argumenty příkazového řádku](main-function-command-line-args.md)
