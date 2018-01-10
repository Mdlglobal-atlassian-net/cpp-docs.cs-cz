---
title: "Vstupní členské funkce datového proudu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3aa6fc5331340c110f2325762bbe46409d53d1b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="input-stream-member-functions"></a>Členské funkce vstupního datového proudu
Členské funkce vstupního datového proudu se používají pro vstup disku. Členské funkce patří:  
  
- [Otevřete funkce pro vstupní datové proudy](#vclrftheopenfunctionforinputstreamsanchor11)  
  
- [Zjištění](#vclrfthegetfunctionanchor12)  
  
- [Getline](#vclrfthegetlinefunctionanchor13)  
  
- [Čtení](#vclrfthereadfunctionanchor14)  
  
- [Seekg – a tellg – funkce](#vclrftheseekgandtellgfunctionsanchor7)  
  
- [Zavřít funkce pro vstupní datové proudy](#vclrftheclosefunctionforinputstreamsanchor15)  
  
##  <a name="vclrftheopenfunctionforinputstreamsanchor11"></a>Otevřete funkce pro vstupní datové proudy  
 Pokud používáte vstupní soubor datového proudu (ifstream), je třeba přidružit k souboru na konkrétní disku tohoto datového proudu. To provedete v konstruktoru, nebo můžete použít **otevřete** funkce. V obou případech argumenty, které jsou stejné.  
  
 Obecně zadáte [ios_base::openmode](../standard-library/ios-base-class.md#openmode) příznak při otevření souboru přidružené vstupního datového proudu (je výchozí režim **ios::in**). Seznam **open_mode** příznaky, viz [open](#vclrftheopenfunctionforinputstreamsanchor11). Příznaků je možné kombinovat s bitová hodnota OR (&#124;) operátor.  
  
 Ke čtení souboru, nejprve použijte **nezdaří** – členská funkce k určení, zda existuje:  
  
```  
istream ifile("FILENAME");

if (ifile.fail())  
// The file does not exist ...  
```  
  
##  <a name="vclrfthegetfunctionanchor12"></a>Zjištění
 Neformátovaný **získat** – členská funkce pracuje stejně jako  **>>**  operátor s dvě výjimky. Nejdřív **získat** funkce obsahuje prázdné znaky, zatímco Extraktor vyloučí mezer při **skipws** je příznak nastaven (výchozí). Druhý, **získat** funkce je méně pravděpodobné, že způsobit vázanou výstupního datového proudu (`cout`, například) zapsány.  
  
 Varianta **získat** funkce určuje adresu vyrovnávací paměti a maximální počet znaků ke čtení. To je užitečné pro omezení počtu znaků odesílané konkrétní proměnné, jak ukazuje tento příklad:  
  
```  
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
  
```  
1234  
```  
  
### <a name="sample-output"></a>Vzorový výstup  
  
```  
1234  
```  
  
##  <a name="vclrfthegetlinefunctionanchor13"></a>Getline
 **Getline** – členská funkce je podobná **získat** funkce. Obě funkce povolit třetí argument, který určuje ukončující znak pro vstup. Výchozí hodnota je znak nového řádku. Obě funkce rezervovat jeden znak pro požadované ukončující znak. Ale **získat** opustí ukončující znak v datovém proudu a **getline** odebere ukončující znak.  
  
 Následující příklad určuje ukončující znak pro vstupní datový proud:  
  
```  
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
  
```  
test  
```  
  
##  <a name="vclrfthereadfunctionanchor14"></a>Čtení
 **Číst** – členská funkce načte bajtů ze souboru do zadané oblasti paměti. Délka argumentu určuje počet přečtených bajtů. Pokud nepoužijete tento argument, čtení zastaví, když je dosaženo fyzického konce souboru nebo v případě souboru textovém režimu, když embedded `EOF` znak je pro čtení.  
  
 Tento příklad čte binární záznam ze souboru mzdy do struktury:  
  
```  
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
  
 Program předpokládá, že jsou formátovány datových záznamů přesně jak je stanoveno struktura s ukončující znaky CR nebo konce řádku.  
  
##  <a name="vclrftheseekgandtellgfunctionsanchor7"></a>Seekg – a tellg – funkce  
 Datové proudy vstupní soubor zachovat interní ukazatel na pozici v souboru, kde dat je další čtení. Nastavit tento ukazatel s `seekg` fungovat, jak je vidět tady:  
  
```  
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
  
 Použít `seekg` implementovat systémy správy data orientovaná na záznamy, vynásobte velikost pevnou délkou záznamů pomocí čísla záznamu získat bajtů pozice relativně ke konci souboru, a pak používat **získat** objektu určeného ke čtení záznam.  
  
 `tellg` – Členská funkce vrátí aktuální pozice v souboru pro čtení. Tato hodnota je typu `streampos`, `typedef` definované v \<iostream >. Následující příklad načte soubor a zobrazí zprávy zobrazující pozic mezer.  
  
```  
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
  
##  <a name="vclrftheclosefunctionforinputstreamsanchor15"></a>Zavřít funkce pro vstupní datové proudy  
 **Zavřete** – členská funkce zavře souboru na disku, který je přidružený vstupní soubor datového proudu a uvolní popisovač souboru operačního systému. [Ifstream](../standard-library/basic-ifstream-class.md) destruktor zavře soubor pro vás, ale můžete použít **zavřete** fungovat, pokud je třeba otevřít jiný soubor pro stejný objekt datového proudu.  
  
## <a name="see-also"></a>Viz také  
 [Vstupní streamy](../standard-library/input-streams.md)

