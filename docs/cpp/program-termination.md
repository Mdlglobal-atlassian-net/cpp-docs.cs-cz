---
title: C++ukončení programu
ms.date: 12/10/2019
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
ms.openlocfilehash: a0e86cacd951327d39296a183be5ee4fbc36fd15
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301337"
---
# <a name="c-program-termination"></a>C++ukončení programu

V C++nástroji můžete ukončit program následujícími způsoby:

- Zavolejte funkci [Exit](exit-function.md) .
- Zavolejte funkci [Abort](abort-function.md) .
- Spustit [návratový](return-statement-cpp.md) příkaz z `main`.

## <a name="exit-function"></a>exit – funkce

Funkce [Exit](../c-runtime-library/reference/exit-exit-exit.md) deklarovaná v \<Stdlib. h > ukončí C++ program. Hodnota zadaná jako argument pro `exit` se vrátí do operačního systému jako návratový kód programu nebo ukončovací kód. Dle konvence návratový kód nula znamená, že byl program dokončen úspěšně. Můžete použít konstanty EXIT_FAILURE a EXIT_SUCCESS, definované v \<Stdlib. h > k indikaci úspěchu nebo neúspěchu programu.

Vydání příkazu **return** z funkce `main` je ekvivalentní volání funkce `exit` s návratovou hodnotou jako její argument.

## <a name="abort-function"></a>abort – funkce

Funkce [Abort](../c-runtime-library/reference/abort.md) , která je deklarována také ve standardním souboru include \<Stdlib. h >, ukončí C++ program. Rozdíl mezi `exit` a `abort` je, že `exit` umožňuje provedení C++ zpracování ukončení za běhu (budou volány globální destruktory objektů), zatímco `abort` program ukončí hned. Funkce `abort` obchází normální proces zničení u inicializovaných globálních statických objektů. Obchází také jakékoli speciální zpracování, které bylo zadáno pomocí funkce [atexit](../c-runtime-library/reference/atexit.md) .

## <a name="atexit-function"></a>atexit – funkce

Pomocí funkce [atexit](../c-runtime-library/reference/atexit.md) můžete zadat akce, které se spustí před ukončením programu. Žádné globální statické objekty inicializované před voláním funkce **atexit** jsou před provedením funkce Exit-Processing zničeny.

## <a name="return-statement-in-main"></a>příkaz return v Main

Vystavení [návratového](return-statement-cpp.md) příkazu z `main` je funkčně ekvivalentní volání funkce `exit`. Vezměte v úvahu v následujícím příkladu:

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

Příkazy `exit` a **return** v předchozím příkladu jsou funkčně stejné. Nicméně C++ vyžaduje, aby funkce, které mají návratové typy jiné než **void** , vracely hodnotu. Příkaz **return** umožňuje vrátit hodnotu z `main`.

## <a name="destruction-of-static-objects"></a>Zničení statických objektů

Když zavoláte `exit` nebo spustíte **návratový** příkaz z `main`, statické objekty jsou zničeny v obráceném pořadí jejich inicializace (po volání `atexit`, pokud existuje). Následující příklad ukazuje, jak taková inicializace a vyčištění funguje.

### <a name="example"></a>Příklad

V následujícím příkladu jsou objekty static `sd1` a `sd2` vytvořeny a inicializovány před vstupem do `main`. Po ukončení tohoto programu pomocí příkazu **return** je nejprve zničena `sd2` a pak `sd1`. Destruktor třídy `ShowData` zavře soubory přidružené k těmto statickým objektům.

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

[main: spuštění programu](main-program-startup.md)