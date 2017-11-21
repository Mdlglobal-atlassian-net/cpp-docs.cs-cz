---
title: "Potenciální chyby při předávání objektů CRT přes hranice knihovny DLL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: DLL conflicts [C++]
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c5fa79de11c7c3a1526fc91361eecdc74f8bdcd7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="potential-errors-passing-crt-objects-across-dll-boundaries"></a>Možné chyby při předávání objektů CRT přes hranice knihovny DLL
Při předání C Run-time (CRT) objekty například popisovače souborů, národní prostředí a proměnných prostředí do nebo z knihovny DLL (volání funkcí přes hranice knihovny DLL), můžete dojít k neočekávanému chování, pokud knihovnu DLL, stejně jako soubory volání do knihovny DLL, používat různé kopie Knihovny CRT.  
  
 Související problému může dojít, když přidělit paměť (buď výslovně `new` nebo `malloc`, nebo implicitně s `strdup`, `strstreambuf::str`a tak dále) a pak předejte ukazatel přes hranice knihovny DLL na uvolnění. Pokud knihovnu DLL a její uživatelé používat různé kopie knihovny CRT to může způsobit poškození porušení nebo haldy přístup k paměti.  
  
 Dalším symptomem tento problém může být chyba v okně výstupu během ladění, jako:  
  
 [] HALDY: Neplatná adresa zadáno RtlValidateHeap(#,#)  
  
## <a name="causes"></a>Způsobí, že  
 Každá kopie knihovny CRT má stav samostatné a odlišné, zachovány v lokální úložiště vláken aplikací nebo DLL. Jako takový CRT objekty například popisovače souborů, proměnných prostředí, a národní prostředí jsou platné pouze pro kopii CRT v aplikaci nebo knihovny DLL, kde jsou tyto objekty přidělené nebo nastavit. Když knihovny DLL a jeho klienty aplikace používají různé kopie knihovny CRT, nelze předat těchto objektů CRT přes hranice knihovny DLL a je chcete být zachyceny správně na druhé straně. To platí hlavně CRT verzí před Universal CRT v sadě Visual Studio 2015 a novější. Došlo specifické pro verzi knihovny CRT pro každou verzi Visual Studia integrovaný s Visual C++ 2013 nebo dřívější. Podrobnosti o interní implementace CRT, například jeho datové struktury a konvence pojmenování, byly odlišné v jednotlivých verzích. Dynamické propojování kódu zkompilovaného pro jednu verzi CRT na jinou verzi knihovny DLL CRT nikdy byl podporován, když příležitostně ho by fungovat, více podle štěstí než záměrné.  
  
 Protože každá kopie knihovny CRT má svou vlastní haldy manager, se v přidělování paměti do jedné knihovny CRT a předání ukazatele přes hranice knihovny DLL na uvolnění jiné kopie knihovny CRT je možnou příčinou poškození haldy. Při navrhování vaší knihovny DLL tak, aby předá objektů CRT přes hranice nebo přidělí paměť a očekává, že má být uvolněno mimo knihovnu DLL, omezíte klienty aplikace knihovny DLL použít stejnou kopii knihovny CRT jako knihovnu DLL. Knihovny DLL a jeho klienty normálně používat stejnou kopii knihovny CRT pouze v případě, že obě jsou propojeny v čas načítání DLL knihovny CRT na stejnou verzi. Vzhledem k tomu, že je DLL verze knihovny Universal CRT používané sady Visual Studio 2015 a později na Windows 10 nyní centrálně nasazené součásti systému Windows, ucrtbase.dll, je stejný pro aplikace vytvořené s nástroji Visual Studio 2015 a novější verze. Ale i v případě, že je stejný jako kód CRT, nelze předání přidělené v jedné haldy součásti, která používá jiný halda paměti.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Tento příklad předá popisovač souboru přes hranice knihovny DLL.  
  
 Soubor DLL a .exe jsou integrované s /MD, takže sdílejí jednu kopii CRT.  
  
 Pokud je znovu sestavit pomocí/MT, aby se použít samostatnou kopii CRT, spuštěna výsledná test1Main.exe výsledky v porušení přístupu.  
  
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
 Tento příklad předá proměnné prostředí přes hranice knihovny DLL.  
  
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
  
 Pokud soubor knihovny DLL i .exe jsou integrované s /MD tak, aby se používá pouze jedné kopie CRT, program úspěšně spuštěn a vytvoří následující výstup:  
  
```  
New MYLIB variable is: c:\mylib;c:\yourlib  
```  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)