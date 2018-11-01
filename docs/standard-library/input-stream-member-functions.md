---
title: Členské funkce vstupního datového proudu
ms.date: 11/04/2016
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
ms.openlocfilehash: b046ea1995d5a8eaa39dced9feb7a5e4c422c253
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663980"
---
# <a name="input-stream-member-functions"></a>Členské funkce vstupního datového proudu

Členské funkce vstupního streamu se používají pro vstup disků. Členské funkce patří:

- [Funkce open pro vstupní datové proudy](#vclrftheopenfunctionforinputstreamsanchor11)

- [Get](#vclrfthegetfunctionanchor12)

- [Getline](#vclrfthegetlinefunctionanchor13)

- [Čtení](#vclrfthereadfunctionanchor14)

- [Seekg – a tellg – funkce](#vclrftheseekgandtellgfunctionsanchor7)

- [Zavřít funkce pro vstupní datové proudy](#vclrftheclosefunctionforinputstreamsanchor15)

## <a name="vclrftheopenfunctionforinputstreamsanchor11"></a> Funkce open pro vstupní datové proudy

Pokud používáte proud vstupní soubor (ifstream), je třeba přidružit k souboru na konkrétní disku tohoto datového proudu. Můžete to provést v konstruktoru, nebo můžete použít `open` funkce. V obou případech argumenty jsou stejné.

Obecně určíte [ios_base::openmode](../standard-library/ios-base-class.md#openmode) příznak po otevření souboru přidruženého vstupního datového proudu (je výchozí režim `ios::in`). Seznam `open_mode` příznaky viz [otevřít](#vclrftheopenfunctionforinputstreamsanchor11). Příznaků je možné kombinovat s bitový operátor OR ( &#124; ) – operátor.

Ke čtení souboru, nejprve pomocí `fail` členskou funkci k určení, zda existuje:

```cpp
istream ifile("FILENAME");

if (ifile.fail())
// The file does not exist ...
```

## <a name="vclrfthegetfunctionanchor12"></a> Get

Neformátovaný `get` členská funkce funguje stejně jako `>>` operátor se dvěma výjimkami. Nejprve je potřeba `get` funkce zahrnuje prázdné znaky, vzhledem k tomu, Extraktor vyloučí prázdné znaky při `skipws` je nastavený příznak (výchozí). Druhý, `get` funkce je méně pravděpodobné, že způsobit vázané výstupního datového proudu (`cout`, například) zapsány.

Varianta `get` funkce určuje adresa vyrovnávací paměti a maximální počet znaků pro čtení. To je užitečné pro omezení počtu znaků odeslané do určité proměnné, jak ukazuje tento příklad:

```cpp
// ioo_get_function.cpp
// compile with: /EHsc
// Type up to 24 characters and a terminating character.
// Any remaining characters can be extracted later.
#include <iostream>
using namespace std;

int main()
{
   char line[25];
   cout << " Type a line terminated by carriage return\n>";
   cin.get( line, 25 );
   cout << line << endl;
}
```

### <a name="input"></a>Vstup

```Input
1234
```

### <a name="sample-output"></a>Vzorový výstup

```Output
1234
```

## <a name="vclrfthegetlinefunctionanchor13"></a> Getline

`getline` Členská funkce je podobný `get` funkce. Obě funkce povolit třetí argument, který určuje ukončujícího znaku pro vstup. Výchozí hodnota je znak nového řádku. Obě funkce vyhradit jeden znak pro požadované ukončujícího znaku. Ale `get` opustí ukončovací znak v datovém proudu a `getline` odebere ukončujícího znaku.

Následující příklad určuje ukončující znak vstupního datového proudu:

```cpp
// getline_func.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char line[100];
   cout << " Type a line terminated by 't'" << endl;
   cin.getline( line, 100, 't' );
   cout << line;
}
```

### <a name="input"></a>Vstup

```Input
test
```

## <a name="vclrfthereadfunctionanchor14"></a> Čtení

`read` Členská funkce přečte bajtů ze souboru k zadané oblasti paměti. Argument délky určuje počet přečtených bajtů. Pokud nezadáte tento argument, zastaví čtení po dosažení fyzické konec souboru nebo v případě režimu textu souboru vložený `EOF` čtením znaku.

V tomto příkladu čte binární záznam ze souboru výplatních pásek do struktury:

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main()
{
   struct
   {
      double salary;
      char name[23];
   } employee;

   ifstream is( "payroll" );
   if( is ) {  // ios::operator void*()
      is.read( (char *) &employee, sizeof( employee ) );
      cout << employee.name << ' ' << employee.salary << endl;
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

Program se předpokládá, že jsou ve formátu záznamů dat přesně jak je uvedeno ve struktuře bez ukončující znaky návrat na začátek řádku a znak odřádkování.

## <a name="vclrftheseekgandtellgfunctionsanchor7"></a> Seekg – a tellg – funkce

Vstupní soubor datové proudy zachovat vnitřní ukazatel pozice v souboru, ve kterém jsou data pro další čtení. Nastavit tento ukazatel `seekg` fungovat, jak je znázorněno zde:

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main( )
{
   char ch;

   ifstream tfile( "payroll" );
   if( tfile ) {
      tfile.seekg( 8 );        // Seek 8 bytes in (past salary)
      while ( tfile.good() ) { // EOF or failure stops the reading
         tfile.get( ch );
         if( !ch ) break;      // quit on null
         cout << ch;
      }
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

Chcete-li použít `seekg` k implementaci systémů pro správu dat orientovaný na záznam, vynásobte velikost záznamu pevné délky pomocí čísla záznamu získat bajtu vzhledem ke konci souboru, a pak použít `get` objektu určeného ke čtení záznamu.

`tellg` Členská funkce vrátí aktuální pozice v souboru pro čtení. Tato hodnota je typu `streampos`, `typedef` definované v \<iostream – >. Následující příklad načte soubor a zobrazí zprávy zobrazující pozice mezery.

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main( )
{
   char ch;
   ifstream tfile( "payroll" );
   if( tfile ) {
       while ( tfile.good( ) ) {
          streampos here = tfile.tellg();
          tfile.get( ch );
          if ( ch == ' ' )
             cout << "\nPosition " << here << " is a space";
       }
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

## <a name="vclrftheclosefunctionforinputstreamsanchor15"></a> Zavřít funkce pro vstupní datové proudy

`close` Členskou funkci souboru na disku, který je přidružený k datovému proudu vstupního souboru se zavře a uvolní popisovač souboru operačního systému. [Ifstream](../standard-library/basic-ifstream-class.md) destruktor zavře soubor, který pro vás, ale můžete použít `close` fungovat, pokud je potřeba otevřít další soubor pro stejný objekt datového proudu.

## <a name="see-also"></a>Viz také:

[Vstupní streamy](../standard-library/input-streams.md)<br/>
