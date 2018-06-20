---
title: Rozsah (C++) | Microsoft Docs
ms.custom: ''
ms.date: 04/08/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], scope
- scope [C++]
- function prototypes [C++], scope
- class scope
- prototype scope
- functions [C++], scope
- scope, C++ names
ms.assetid: 81fecbb0-338b-4325-8332-49f33e716352
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e79ae7f861553ce2bcd7bee6cbb14a3c2965d4ce
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238757"
---
# <a name="scope-c"></a>Rozsah (C++)

Při deklaraci elementu programu, jako jsou třídy, funkce nebo proměnná, můžete jeho název pouze "Zobrazit" a používají v některých částech vašeho programu. Kontext, ve kterém je vidět název nazývá jeho *oboru*. Například, pokud je deklarovat proměnnou `x` v rámci funkce, `x` se zobrazí v rámci této tělo funkce. Má *místní rozsah*. Může mít jiné proměnné se stejným názvem v programu; jako, které jsou v různých oborech, jejich není v rozporu jedno pravidlo definice a je vyvolána žádná chyba.

Pro automatické proměnné nestatické oboru také určuje, kdy se vytváří a zničen v paměti pro programy. 

Existují šesti druhy oboru:

- **Globální obor** globální název je ten, který je deklarován mimo všechny třídy, funkce nebo obor názvů. V jazyce C++ však i tyto názvy existovat s implicitní globální obor názvů. Obor názvů globální rozšiřuje z bodu deklarace na konec souboru, ve které jsou deklarované. Globální názvy, viditelnost také řídí pravidly z [propojení](program-and-linkage-cpp.md) které určují, zda je název viditelné v další soubory v programu.

- **Namespace oboru** název, který je deklarované v rámci [obor názvů](namespaces-cpp.md), mimo žádné definice třídy nebo výčtu nebo funkce bloku je viditelná z bodu deklarace na konec oboru názvů. Obor názvů může definovat v více bloků v rámci různých souborů.

- **Místní rozsah** název deklarované v rámci funkce nebo lambda, včetně názvů parametrů mít místní rozsah. Budou se často označuje jako "místní hodnoty". Jsou viditelné z jejich bod deklarace na konec tělo funkce nebo lambda. Místní rozsah je druh rozsah bloku, která je popsána dále v tomto článku.

- **Třída oboru** názvy členů třídy mají rozsah třídy, která rozšiřuje v definici třídy bez ohledu na bod deklarace. Usnadnění člena třídy se další řízené **veřejné**, **privátní**, a **chráněné** klíčová slova. Veřejné nebo chráněné členy jsou přístupné pouze pomocí operátory výběru členů (**.** nebo **->**) nebo operátory ukazatelů na členy (**.\***  nebo **-> \***).

- **Příkaz oboru** názvy deklarované v **pro**, **Pokud**, **při**, nebo **přepínač** příkaz jsou viditelné až do konce příkaz bloku.

- **Funkce oboru** A [popisek](labeled-statements.md) má funkce obor, což znamená, je zobrazen v celé tělo funkce ještě před jeho bod deklarace. Rozsah funkce umožňuje zapsat jako příkazy `goto cleanup` před `cleanup` popisek je deklarován.

## <a name="hiding-names"></a>Skrytí názvů

Název lze skrýt jeho deklarací v uzavřeném bloku. Na následujícím obrázku je `i` deklarováno v rámci vnitřního bloku, a tím dojde ke skrytí proměnné přidružené k `i` v rozsahu vnějšího bloku.

 ![Blok&#45;obor název skrytí](../cpp/media/vc38sf1.png "vc38SF1") rozsah bloku a skrytí název

 Výstup z programu zobrazeného na obrázku je:

```cpp
i = 0
i = 7
j = 9
i = 0
```

> [!NOTE]
> Argument `szWhat` je považován za argument nacházející se v oboru funkce. Proto je zpracováván stejně, jako by byl deklarován v nejvzdálenějším bloku funkce.

## <a name="hiding-class-names"></a>Skrytí názvy tříd

 Názvy tříd lze skrýt deklarováním funkce, objektu, proměnné nebo enumerátoru ve stejném oboru. Ale název třídy můžete v případě dál dostat předponu klíčové slovo **třída**.

```cpp
// hiding_class_names.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

// Declare class Account at global scope.
class Account
{
public:
    Account( double InitialBalance )
        { balance = InitialBalance; }
    double GetBalance()
        { return balance; }
private:
    double balance;
};

double Account = 15.37;            // Hides class name Account

int main()
{
    class Account Checking( Account ); // Qualifies Account as 
                                       //  class name

    cout << "Opening account with balance of: "
         << Checking.GetBalance() << "\n";
}
//Output: Opening account with balance of: 15.37
```

> [!NOTE]
> Některé umístit název třídy (`Account`) je volána pro třídu – klíčové slovo použije k odlišení od globální obor proměnné účtu. Toto pravidlo neplatí, vyskytne-li se název třídy na levé straně operátoru rozlišení oboru (::). Názvy na levé straně operátoru rozlišení oboru jsou vždy považovány za názvy tříd.

 Následující příklad ukazuje, jak deklarovat ukazatel na objekt typu `Account` pomocí **třída** – klíčové slovo:

```cpp
class Account *Checking = new class Account( Account );
```

 `Account` v inicializátoru (v závorkách) v předchozím příkazu, má globální obor; je typu **dvojité**.

> [!NOTE]
> Opětovné použití názvů identifikátorů, jak je znázorněno v tomto příkladu, je považováno za špatný styl programování.

 Další informace o ukazatelích najdete v tématu [odvozené typy](http://msdn.microsoft.com/en-us/aa14183c-02fe-4d81-95fe-beddb0c01c7c). Informace o deklarace a inicializace třídy objektů najdete v tématu [tříd, struktur a sjednocení](../cpp/classes-and-structs-cpp.md). Informace o používání **nové** a **odstranit** bez úložiště operátory najdete v tématu [nové a odstraňte operátory](new-and-delete-operators.md).

## <a name="hiding-names-with-global-scope"></a>Skrytí názvy s globálním rozsahem

 Názvy s globálním rozsahem můžete skrýt explicitně deklarace stejný název v oboru bloku. Ale globálního oboru názvů lze přistupovat pomocí operátor řešení rozsahu (`::`).

```cpp
#include <iostream>

int i = 7;   // i has global scope, outside all blocks
using namespace std;

int main( int argc, char *argv[] ) {
   int i = 5;   // i has block scope, hides i at global scope
   cout << "Block-scoped i has the value: " << i << "\n";
   cout << "Global-scoped i has the value: " << ::i << "\n";
}
```

```Output
Block-scoped i has the value: 5
Global-scoped i has the value: 7
```

## <a name="see-also"></a>Viz také

 [Základní koncepty](../cpp/basic-concepts-cpp.md)