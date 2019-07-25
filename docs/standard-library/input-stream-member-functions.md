---
title: Členské funkce vstupního datového proudu
ms.date: 07/19/2019
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
ms.openlocfilehash: b846ff177f3032d81e5c81a39a0111c73a1750fb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452075"
---
# <a name="input-stream-member-functions"></a>Členské funkce vstupního datového proudu

Členské funkce vstupního datového proudu se používají pro vstup disku.

## <a name="vclrftheopenfunctionforinputstreamsanchor11"></a>otevírají

Pokud používáte datový proud vstupního souboru (`ifstream`), musíte tento datový proud přidružit k určitému souboru na disku. Můžete to provést v konstruktoru nebo můžete použít `open` funkci. V obou případech jsou argumenty stejné.

Při otevření souboru přidruženého ke vstupnímu datovému proudu je obecně nutné zadat příznak [ios_base:: openmode](../standard-library/ios-base-class.md#openmode) (výchozí režim je `ios::in`). Seznam `openmode` příznaků naleznete v tématu [ios_base:: openmode](../standard-library/ios-base-class.md#openmode). Příznaky lze kombinovat pomocí operátoru OR ( &#124; ).

Chcete-li číst soubor, nejprve pomocí `fail` členské funkce určete, zda existuje:

```cpp
istream ifile("FILENAME");

if (ifile.fail())
// The file does not exist ...
```

## <a name="vclrfthegetfunctionanchor12"></a>Čtěte

Neformátovaná `get` členská funkce funguje `>>` jako operátor se dvěma výjimkami. Za prvé, `get` funkce obsahuje prázdné znaky, zatímco extraktor `skipws` při nastavení příznaku nevylučuje prázdné místo (výchozí). Za druhé, `get` funkce je méně pravděpodobný způsob, jak vyprázdnit vázaný`cout`výstupní datový proud (například).

Variace `get` funkce určuje adresu vyrovnávací paměti a maximální počet znaků, které se mají přečíst. To je užitečné pro omezení počtu znaků odesílaných konkrétní proměnnou, jak ukazuje tento příklad:

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

## <a name="vclrfthegetlinefunctionanchor13"></a>getline

Členská funkce je podobná `get` funkci. `getline` Obě funkce povolují třetí argument, který určuje ukončovací znak pro vstup. Výchozí hodnota je znak nového řádku. Obě funkce vyhradí jeden znak pro požadovaný ukončovací znak. Ale opustí ukončovací znak v proudu a `getline` odstraní ukončovací znak. `get`

Následující příklad určuje ukončovací znak pro vstupní datový proud:

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

## <a name="vclrfthereadfunctionanchor14"></a>oprávnění

`read` Členská funkce přečte bajty ze souboru do zadané oblasti paměti. Argument Length určuje počet čtených bajtů. Pokud tento argument nezadáte, přečtení se zastaví, když je dosaženo fyzického konce souboru, nebo v případě souboru textového režimu, když je načten vložený `EOF` znak.

Tento příklad přečte binární záznam ze souboru mzdy do struktury:

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

Program předpokládá, že datové záznamy jsou formátovány přesně tak, jak jsou určeny strukturou bez ukončujícího návratového znaku nebo znaků kanálu řádku.

## <a name="vclrftheseekgandtellgfunctionsanchor7"></a>seekg a tellg

Datové proudy vstupních souborů udržují interní ukazatel na pozici v souboru, kde se mají číst data v dalším umístění. Tento ukazatel nastavíte pomocí `seekg` funkce, jak je znázorněno zde:

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

Chcete- `seekg` li použít pro implementaci systémů pro správu dat orientovaných na záznamy, vynásobte velikost záznamu pevné délky číslem záznamu pro získání pozice bajtů relativně ke konci souboru a pak `get` použijte objekt pro načtení záznamu.

`tellg` Členská funkce vrátí pozici aktuálního souboru pro čtení. Tato hodnota je typu `streampos`, který `typedef` je definován v \<iostream – >. Následující příklad přečte soubor a zobrazí zprávy ukazující pozice mezer.

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

## <a name="vclrftheclosefunctionforinputstreamsanchor15"></a>uzavírací

`close` Členská funkce zavře soubor disku, který je přidružený ke vstupnímu streamu vstupních souborů, a uvolní popisovač souborů operačního systému. Destruktor soubor zavře za vás, ale `close` funkci můžete použít, pokud potřebujete otevřít jiný soubor pro stejný objekt streamu. [`ifstream`](../standard-library/basic-ifstream-class.md)

## <a name="see-also"></a>Viz také:

[Vstupní streamy](../standard-library/input-streams.md)
