---
title: Řetězcový literál | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- string literals
- strings [C++], string literals
ms.assetid: 6d1fc3f8-0d58-4d68-9678-16b4f6dc4766
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 41f1996cd4f4caf24ac08d09b05e636cb09f7eed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415262"
---
# <a name="string-literal"></a>Řetězcový literál

Zpracování řetězcové literály se změnila od spravovaných rozšíření jazyka C++ na Visual C++.

Ve spravovaných rozšíření pro návrh jazyka C++, byl označen zahájením literálu řetězce s spravované řetězcového literálu `S`. Příklad:

```
String *ps1 = "hello";
String *ps2 = S"goodbye";
```

Výkon režii mezi dvěma inicializace se ukázalo netriviální, jako soubor CIL se NAČTE následující reprezentaci ukazuje, jak je vidět **ildasm**:

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

To je znatelné úspory pouze zapamatování (nebo learning) jako předpona řetězcový literál s `S`. V nové syntaxi zpracování řetězcové literály se provádí transparentní, určit podle kontextu použití. `S` Už musí být zadaná.

A co případy, kdy budeme potřebovat explicitně směrovat kompilátor k interpretaci jedné nebo jiného? V těchto případech doporučujeme použít explicitní přetypování. Příklad:

```
f( safe_cast<String^>("ABC") );
```

Kromě toho teď odpovídá řetězcového literálu `String` pomocí jednoduchého převodu, nikoli standardní převod. Když to nemusí znít jako mnohem změní řešení sady přetížené funkce, mezi které patří `String` a `const char*` jako konkurenční formální parametry. Jednou přeložit na řešení `const char*` instance nyní je označeno jako dvojznačné. Příklad:

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

Proč je nějaký rozdíl? Od více než jednu instanci s názvem `f` existuje v rámci programu, k tomu je potřeba algoritmus pro použít pro volání rozlišení přetížení funkce. Formální rozlišení přetížení funkce zahrnuje tři kroky.

1. Kolekce kandidátské funkce. Funkce Release candidate jsou tyto metody v rámci oboru, které lexikálně shodovat s názvem volanou funkci. Například od `f()` vyvolané prostřednictvím instance `R`, všechny pojmenované funkce `f` , které nejsou členem `R` (nebo její základní třídy hierarchie) nejsou kandidátské funkce. V našem příkladu jsou dva kandidátské funkce. Toto jsou dva členské funkce `R` s názvem `f`. Volání selže v průběhu této fáze, pokud je sada funkcí Release candidate prázdná.

1. Sada přijatelné funkcí z kandidátské funkce. Přijatelné funkce je ten, který lze vyvolat pomocí zadaných ve volání, daný počet argumentů a jejich typy argumentů. V našem příkladu jsou obě funkce kandidáta také přijatelné funkce. Volání selže v průběhu této fáze, pokud je sada funkcí přijatelné prázdná.

1. Vyberte funkce, která představuje nejlepší shodu volání. To se provádí hodnocení k transformaci argumenty, které mají typ přijatelné funkčních parametrů použitých převodů. To je poměrně jednoduché pomocí jediného parametru funkce; bude poněkud složitější, pokud existuje více parametrů. Volání selže v průběhu této fáze, pokud není nalezena žádná nejlepší shoda. To znamená pokud jsou stejně dobrým převody potřebné pro převod typu je skutečný argument typu formálního parametru. Volání je označeno jako dvojznačné.

Ve spravovaných rozšíření na řešení tohoto volání vyvolat `const char*` instance jako nejlepší shoda. V nové syntaxi, převod nezbytné tak, aby odpovídaly `"abc"` k `const char*` a `String^` jsou teď rovnocenné – to znamená, stejně dobrým – a proto volání je označeno jako chybné – to znamená, jako dvojznačné.

Důsledkem je nás dvě otázky:

- Co je typ argumentu, `"abc"`?

- Jaký je algoritmus pro určení, kdy je lepší než jiné jeden typ převodu?

Typ řetězcového literálu `"abc"` je `const char[4]` – mějte na paměti, je implicitní null ukončující znak na konci každého řetězce literálu.

Algoritmus pro určení, kdy je lepší než jiné jeden typ převodu zahrnuje umístění převody možných typů v hierarchii. Tady je Moje principy této hierarchii – všechny tyto převody samozřejmě jsou implicitní. Zápisem explicitní přetypování pomocí přepsání podobným způsobem, jakým hierarchie závorky přepíše prioritu obvykle operátor výrazu.

1. Přesná shoda je nejvhodnější. Logicky pro argument přesně shodovat, nemusí přesně odpovídat typu parametru; právě musí být dostatečně blízko. Toto je klíčem k pochopení, co se děje v tomto příkladu a jak je změnit jazyk.

1. V rámci propagační akce je lepší než standardní převod. Například zvýšení úrovně `short int` do `int` je lepší než převod `int` do `double`.

1. Standardní převod je lepší než převod na uzavřené určení. Například převod `int` do `double` je lépe zabalení `int` do `Object`.

1. Převod na uzavřené určení je lepší než implicitního uživatelem definovaného převodu. Například zabalení `int` do `Object` je lepší než použití operátoru převodu `SmallInt` hodnotu třídy.

1. Implicitní převod definovaný uživatelem, je lepší než převod vůbec. Implicitní převod definovaný uživatelem je poslední ukončovací před chybou (s výstrahou, že formální podpis může obsahovat pole parametrů a tlačítko se třemi tečkami na této pozici).

To co znamená říct, že přesná shoda není nutně přesně odpovídající? Například `const char[4]` přesně neodpovídá buď `const char*` nebo `String^`, a ještě je náš příklad Nejednoznačnost mezi dva konfliktní přesné shody.

Přesná shoda, jakmile k ní dojde, obsahuje několik triviální převodů. Existují čtyři jednoduché převody podle ISO-C++, které mohou být použity a stále kvalifikovat jako přesnou shodu. Tři jsou označovány jako l-hodnoty transformace. Čtvrtý typ se nazývá převod kvalifikace. Tři transformace l-hodnoty jsou považovány za lépe přesná shoda než ta, vyžadují převod kvalifikace.

Jednu formu l-hodnoty transformace je převod nativní pole na ukazatel. To je, co se účastní porovnávání `const char[4]` k `const char*`. Proto se shoda `f("abc")` k `f(const char*)` najít přesnou shodu. V dřívějších ztělesněních náš jazyk ve skutečnosti jednalo nejlepší shodu.

Kompilátor, aby Příznak volání jako nejednoznačné, vyžaduje, aby převod `const char[4]` k `String^` také být přesnou shodou prostřednictvím jednoduchého dotazu převodu. Toto je změna, která byla zavedena v nové verzi jazyka. A to je důvod, proč volání je nyní označena jako dvojznačné.

## <a name="see-also"></a>Viz také

[Obecné jazykové změny (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[řetězec](../windows/string-cpp-component-extensions.md)