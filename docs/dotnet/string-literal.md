---
title: "Řetězcový literál | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- string literals
- strings [C++], string literals
ms.assetid: 6d1fc3f8-0d58-4d68-9678-16b4f6dc4766
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dd62f85b87473d1371daf2d2fa009d8620e59b57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="string-literal"></a>Řetězcový literál
Zpracování textových literálů změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 V spravovaných rozšíření pro návrh jazyka C++, byl označen zahájením literálu řetězce s literál řetězce `S`. Příklad:  
  
```  
String *ps1 = "hello";  
String *ps2 = S"goodbye";  
```  
  
 Výkon režie mezi dvěma inicializacích jím být netriviální, jako následující soubor CIL ukazuje vyobrazení **ildasm**:  
  
```  
// String *ps1 = "hello";  
ldsflda    valuetype $ArrayType$0xd61117dd  
     modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier)   
     '?A0xbdde7aca.unnamed-global-0'  
  
newobj instance void [mscorlib]System.String::.ctor(int8*)  
stloc.0  
  
// String *ps2 = S"goodbye";  
ldstr      "goodbye"  
stloc.0  
```  
  
 Znatelné úspory právě zapamatování (nebo learning) jako předpona řetězcového literálu, je pomocí `S`. V nové syntaxe zpracování textových literálů není provedena transparentní, určit podle kontextu použít. `S` Už je třeba zadat.  
  
 Co o případy, ve kterých je potřeba explicitně nasměrovat kompilátor k jedné nebo druhé interpretaci? V těchto případech použijeme explicitní přetypování. Příklad:  
  
```  
f( safe_cast<String^>("ABC") );  
```  
  
 Kromě toho nyní odpovídá řetězcový literál `String` pomocí jednoduchého převodu na rozdíl od standardní převod. Když to nemusí zvukových jako mnohem změní řešení sad přetížené funkce, mezi které patří `String` a `const char*` jako konkurenční formální parametry. Jednou přeložit na řešení `const char*` instance nyní je označeno jako dvojznačné. Příklad:  
  
```  
ref struct R {  
   void f(const char*);  
   void f(String^);  
};  
  
int main () {  
   R r;  
   // old syntax: f( const char* );  
   // new syntax: error: ambiguous  
   r.f("ABC");   
}  
```  
  
 Proč je nějaký rozdíl? Od více než jednu instanci s názvem `f` existuje v rámci programu, to vyžaduje, aby algoritmus rozlišení přetížení funkce má být použita pro volání. Formální rozlišení přetížení funkce zahrnuje tři kroky.  
  
1.  Kolekce kandidátských funkcí. Kandidátských funkcí jsou tyto metody v rámci oboru, které lexikálně shodovat s názvem volanou funkci. Například od `f()` volání prostřednictvím instance `R`, všechny funkce s názvem `f` nejsou členem `R` (nebo její základní třída hierarchie) nejsou kandidátských funkcí. V našem příkladu jsou dvě funkce candidate. Toto jsou dva členské funkce z `R` s názvem `f`. V průběhu této fáze se volání nezdaří, pokud je sada funkcí candidate prázdná.  
  
2.  Sada přijatelná funkce z kandidátských funkcí. Vhodným funkce je ten, který lze vyvolat pomocí zadanou ve volání, získá počet argumentů a jejich typy argumentů. V našem příkladu jsou obě funkce candidate také vhodným funkce. Volání selže v průběhu této fáze, pokud sada přijatelná funkce je prázdný.  
  
3.  Vyberte funkce, která představuje nejlepší shodu volání. K tomu je potřeba hodnocením převodů, použitých k transformaci argumenty, které mají typ parametry použitelné funkce. Toto je poměrně jednoduché pomocí jediného parametru funkce; bude poněkud složitější, pokud existuje několik parametrů. V průběhu této fáze se volání nezdaří, pokud není nalezena žádná nejlepší shoda. To znamená pokud jsou nezbytné pro převod typu argument skutečný typ formálního parametru převody stejně vhodné. Volání je označeno jako dvojznačné.  
  
 Ve spravovaných rozšíření rozlišení tohoto volání vyvolalo `const char*` instance jako nejlepší shodu. V nové syntaxe, převod potřeby tak, aby odpovídaly `"abc"` k `const char*` a `String^` jsou nyní ekvivalentní – to znamená, je stejně dobrý – a proto volání je označeno jako chybné – to znamená, jako nejednoznačný.  
  
 To nám vede ke dvěma otázky:  
  
-   Co je typ skutečného argumentu `"abc"`?  
  
-   Jaký je algoritmus pro určení, kdy je lepší, než jiné jeden typ převodu?  
  
 Typ řetězcový literál `"abc"` je `const char[4]` -Pamatujte si, že je literál implicitní null ukončující znak na konci každého řetězce.  
  
 Algoritmus pro určení, kdy je lepší, než jiné jeden typ převodu zahrnuje umístění možných převodů typů v hierarchii. Zde je mé porozumění hierarchii – všechny tyto převody samozřejmě jsou implicitní. Pomocí zápisu explicitního přetypování přepíše hierarchii podobným způsobem, kulaté závorky přepsání obvyklé operátorů výrazu.  
  
1.  Nejlepší je přesnou shodu. Logicky pro argumentu přesně shodovat, se nemusí přesně shodovat s typem parametru; právě musí být dostatečně zavřít. Toto je klíčem k pochopení, co se děje v tomto příkladu a jak došlo ke změně jazyka.  
  
2.  U povýšení je lepší, než standardní převod. Například povýšení `short int` k `int` je lepší, než převod `int` do `double`.  
  
3.  Standardní převod je lepší, než převod zabalením. Například převod `int` do `double` je lepší, který zabalení `int` do `Object`.  
  
4.  Převod zabalením je lepší, než implicitní převod definovaný uživatelem. Například zabalení `int` do `Object` je lepší, než použití operátoru převodu `SmallInt` třídy hodnoty.  
  
5.  Implicitní převod definovaný uživatelem, je lepší, než žádný převod vůbec. Implicitní převod definovaný uživatelem je posledním únikem před chybou (s přímý přístup do paměti, že formální podpis může obsahovat pole parametrů nebo třemi tečkami na této pozici).  
  
 Ano co to znamená, to znamená, že přesná shoda není nutně přesně odpovídající? Například `const char[4]` přesně neodpovídá buď `const char*` nebo `String^`, a zatím v našem příkladu nejednoznačnosti je mezi dvěma konfliktní přesné shody!  
  
 Přesná shoda, jak se to stává, zahrnuje několik trivial převody. Existují čtyři triviální převody pod ISO-C++, který můžete použít a stále kvalifikaci jako přesnou shodu. Tři se označují jako lvalue transformace. Čtvrtý typ se nazývá převod kvalifikace. Tři transformace lvalue jsou považovány za lepší přesnou shodu než jeden vyžadují převod kvalifikace.  
  
 Jednu formu transformace lvalue je převod nativní pole na ukazatel. Toto je postup při porovnávání `const char[4]` k `const char*`. Proto je shoda mezi `f("abc")` k `f(const char*)` je přesnou shodu. V dřívějších ztělesněních naše jazyk ve skutečnosti šlo nejlepší shodu.  
  
 Kompilátor pro označení volání jako dvojznačného vyžaduje, aby převodu `const char[4]` k `String^` také být přesnou shodu prostřednictvím triviálního převodu. Toto je změna, která byla zavedena v nové verzi jazyka. A z tohoto důvodu volání je nyní označeno jako nejednoznačný.  
  
## <a name="see-also"></a>Viz také  
 [Obecné jazykové změny (C + +/ CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [Řetězec](../windows/string-cpp-component-extensions.md)