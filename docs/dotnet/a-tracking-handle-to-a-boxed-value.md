---
title: Sledovací popisovač zabalené hodnoty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- boxed value types, tracking handle to
ms.assetid: 16c92048-5b74-47d5-8eca-dfea3d38879a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c7e26efae93b509700c3bb0c992d9f397559e99f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380723"
---
# <a name="a-tracking-handle-to-a-boxed-value"></a>Sledovací popisovač zabalené hodnoty

Využití sledovací popisovač odkaz na typ hodnoty se změnila od spravovaných rozšíření jazyka C++ na Visual C++.

Zabalení je zvláštností systému typů CLR unified. Typy hodnot přímo obsahovat jejich stavu, typy odkazů jsou implicitní pár: pojmenovaná entita je popisovač pro objekt nepojmenované přidělena na spravované haldě. Jakákoli inicializace nebo přiřazení hodnoty, typ, který `Object`, například vyžaduje, že typ hodnoty lze umístit haldu CLR – to je nastává bitová kopie zabalení - nejprve přidělením paměti přidružené pak tak, že zkopíruje typ hodnoty stavu a pak vrací adresu této anonymní hybridní hodnoty nebo odkazu. To znamená, když jeden zapisuje v jazyce C#

```cpp
object o = 1024; // C# implicit boxing
```

je zajistí další děje než provádí zřejmý zjednodušení kódu. Návrh jazyka C# maskuje složitost nejen jaké operace trvá pod pokličkou, ale také abstrakce samotného zabalení. Spravovaná rozšíření pro C++, na druhé straně obavy, že to by mohlo dojít k o efektivitu, vloží jej do tváře uživatele tím, že vyžaduje explicitní instrukce:

```cpp
Object *o = __box( 1024 ); // Managed Extensions explicit boxing
```

Zabalení je implicitní v jazyce Visual C++:

```cpp
Object ^o = 1024; // new syntax implicit boxing
```

`__box` – Klíčové slovo slouží důležité služby v rámci spravovaného rozšíření, která chybí záměrné z jazyků, jako je C# a Visual Basic: poskytuje slovník i sledování zpracování pro přímé manipulace s pevně určené instance na spravované haldě. Představte si třeba následující malý program:

```cpp
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

Podkladový kód generovaný pro tři vyvolání `WriteLine` zobrazit různé ceny za přístup k hodnotě zabalené hodnoty typu (díky Yves Dolce pro upozornění na tyto rozdíly), kde označenými řádky zobrazit režie spojené s jednotlivými vyvolání.

```cpp
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

Předávání hodnotový typu přímo do `Console::WriteLine` eliminuje zabalení a nutnosti vyvolání `ToString()`. (Samozřejmě, je dřívější zabalení inicializovat `br`, takže jsme něco nezískali, pokud máme opravdu `br` pracovat.

V nové syntaxi podpora pro pevně určené typy hodnot je výrazně více elegantnímu a integrované v rámci systému typů a přitom zachovat jeho výkon. Tady je například překlad starší malý program:

```cpp
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

[Hodnotové typy a jejich chování (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[Postupy: Explicitní žádost o zabalení](../dotnet/how-to-explicitly-request-boxing.md)