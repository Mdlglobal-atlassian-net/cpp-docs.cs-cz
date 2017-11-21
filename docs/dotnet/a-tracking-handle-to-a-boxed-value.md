---
title: "Sledovací popisovač zabalené hodnoty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: boxed value types, tracking handle to
ms.assetid: 16c92048-5b74-47d5-8eca-dfea3d38879a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a986dcea2eec183ae09eb9af275082922257ef76
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="a-tracking-handle-to-a-boxed-value"></a>Sledovací popisovač zabalené hodnoty
Použití sledovací popisovač odkaz na typ hodnoty změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Zabalení je typickým znakem systému typ CLR unified. Typy hodnot přímo obsahují jejich stav, zatímco odkazové typy jsou implicitní pár: pojmenované entita je popisovač pro objekt nepojmenované přidělené na spravované haldě. Jakákoli inicializace nebo přiřazení hodnoty typ, který má `Object`, například třeba, aby typ hodnoty uloženy v rámci haldy CLR - Toto je nastává bitová kopie zabalení – nejprve přidělením přidružené paměti a potom zkopírováním typ hodnoty stavu a potom vrátí adresu tento anonymní hybridní hodnotu nebo odkaz. Proto když jeden zapisuje v jazyce C#  
  
```  
object o = 1024; // C# implicit boxing  
```  
  
 je značnou část Další přejdete než je provedené zřejmá jednoduchost kódu. Návrh jazyka C# skrývá složitosti nejen jakým operacím trvá pod pokličkou, ale také abstrakce samotného zabalení. Spravovaná rozšíření pro C++ na druhé straně obavy, že to by vedlo k false představu o efektivitu, vloží ho stojíte uživatele před tím, že vyžaduje explicitní instrukce:  
  
```  
Object *o = __box( 1024 ); // Managed Extensions explicit boxing  
```  
  
 Zabalení je implicitní v jazyce Visual C++:  
  
```  
Object ^o = 1024; // new syntax implicit boxing  
```  
  
 `__box` – Klíčové slovo poskytuje zásadní službu v rámci spravovaných rozšíření, která chybí záměrné z jazyků, například C# a Visual Basic: poskytuje slovník i sledování zpracování pro přímá manipulace s zabalené instanci na spravovaná halda. Zvažte například následující malý program:  
  
```  
int main() {  
   double result = 3.14159;  
   __box double * br = __box( result );  
  
   result = 2.7;   
   *br = 2.17;     
   Object * o = br;  
  
   Console::WriteLine( S"result :: {0}", result.ToString() ) ;  
   Console::WriteLine( S"result :: {0}", __box(result) ) ;  
   Console::WriteLine( S"result :: {0}", br );  
}  
```  
  
 Základní kód generovaný pro tři vyvolání `WriteLine` zobrazit různé nákladů na přístup k hodnotě zabalené hodnoty typu (díky Yves Dolce pro odkazující na tyto rozdíly), kde uvedené řádky ukazují režie spojená s jednotlivými volání.  
  
```  
// Console::WriteLine( S"result :: {0}", result.ToString() ) ;  
ldstr      "result :: {0}"  
ldloca.s   result  // ToString overhead  
call       instance string  [mscorlib]System.Double::ToString()  // ToString overhead  
call       void [mscorlib]System.Console::WriteLine(string, object)  
  
// Console::WriteLine( S"result :: {0}", __box(result) ) ;  
Ldstr    " result :: {0}"  
ldloc.0  
box    [mscorlib]System.Double // box overhead  
call    void [mscorlib]System.Console::WriteLine(string, object)  
  
// Console::WriteLine( S"result :: {0}", br );  
ldstr    "result :: {0}"  
ldloc.0  
call     void [mscorlib]System.Console::WriteLine(string, object)  
```  
  
 Předání typu zabalené hodnoty přímo na `Console::WriteLine` eliminuje zabalení a potřeba vyvolání `ToString()`. (Samozřejmě, je dřívější zabalení pro inicializaci `br`, takže jsme nic nezískali, pokud opravdu vložíme `br` pracovat.  
  
 V nové syntaxe je podpora pro pevně určené typy hodnot podstatně více elegantní a integrovaná v rámci systému typ při zachování jejich síly. Zde je ukázka, překlad starší malé programu:  
  
```  
int main()  
{  
   double result = 3.14159;  
   double^ br = result;  
   result = 2.7;  
   *br = 2.17;  
   Object^ o = br;  
   Console::WriteLine( "result :: {0}", result.ToString() );  
   Console::WriteLine( "result :: {0}", result );  
   Console::WriteLine( "result :: {0}", br );  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Hodnotové typy a jejich chování (C + +/ CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Postupy: explicitní žádost o zabalení](../dotnet/how-to-explicitly-request-boxing.md)