---
title: Rozsah (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- classes [C++], scope
- scope [C++]
- function prototypes [C++], scope
- class scope
- prototype scope
- functions [C++], scope
- scope, C++ names
ms.assetid: 81fecbb0-338b-4325-8332-49f33e716352
ms.openlocfilehash: a5b5601c89991fbe1a148ebaf781fe2ad6a9dfc4
ms.sourcegitcommit: c4cf8976939dd0e13e25b82930221323ba6f15d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83204140"
---
# <a name="scope-c"></a>Rozsah (C++)

Pokud deklarujete prvek programu, jako je například třída, funkce nebo proměnná, jeho název může být "zobrazen" a bude použit v určitých částech programu. Kontext, ve kterém je název viditelný, se nazývá jeho *obor*. Například pokud deklarujete proměnnou `x` v rámci funkce, `x` je viditelné pouze v rámci této části funkce. Má *místní rozsah*. V programu můžete mít jiné proměnné se stejným názvem. Pokud jsou v různých oborech, neporušily jedno pravidlo definice a nevyvolává se žádná chyba.

Pro automatické nestatické proměnné rozsah také určuje, kdy jsou vytvořeny a zničeny v paměti programu.

Existuje šest druhů rozsahu:

- **Globální rozsah** Globální název je deklarovaný mimo jakoukoliv třídu, funkci nebo obor názvů. V jazyce C++ však i tyto názvy existují s implicitním globálním oborem názvů. Rozsah globálních názvů sahá z bodu deklarace na konec souboru, ve kterém jsou deklarovány. U globálních názvů se viditelnost řídí také pravidly [propojení](program-and-linkage-cpp.md) , která určují, zda je název viditelný v jiných souborech v programu.

- **Obor názvů** Název, který je deklarován v rámci [oboru názvů](namespaces-cpp.md), mimo jakoukoliv třídu nebo definici výčtu nebo blok funkce, je viditelný z jeho bodu deklarace na konci oboru názvů. Obor názvů může být definován ve více blocích napříč různými soubory.

- **Místní rozsah** Název deklarovaný v rámci funkce nebo výrazu lambda, včetně názvů parametrů, má místní rozsah. Jsou často označovány jako "místní". Jsou viditelné pouze z místa deklarace na konci funkce nebo těla výrazu lambda. Místní obor je druh oboru bloku, který je popsán dále v tomto článku.

- **Rozsah třídy** Názvy členů třídy mají obor třídy, který rozšiřuje celou definici třídy bez ohledu na bod deklarace. Přístupnost člena třídy je dále kontrolována pomocí klíčových slov **Public**, **Private**a **Protected** . Veřejné nebo chráněné členy mohou být přístupné pouze pomocí operátorů výběru členů (**.** nebo **->** ) nebo operátory pointer-to-Member (**.** <strong>\*</strong> nebo **->** <strong>\*</strong> ).

- **Obor příkazu** Názvy deklarované v příkazu **for**, **if**, **while**nebo **Switch** jsou viditelné až do konce bloku příkazu.

- **Rozsah funkce** [Popisek](labeled-statements.md) má rozsah funkce, což znamená, že je viditelný v celé tělo funkce, a to i před jeho bodem deklarace. Rozsah funkce umožňuje napsat příkazy, jako `goto cleanup` předtím, než `cleanup` je popisek deklarován.

## <a name="hiding-names"></a>Skrytí názvů

Název lze skrýt jeho deklarací v uzavřeném bloku. Na následujícím obrázku je `i` deklarováno v rámci vnitřního bloku, a tím dojde ke skrytí proměnné přidružené k `i` v rozsahu vnějšího bloku.

![Skrytí názvu oboru&#45;bloku](../cpp/media/vc38sf1.png "Skrytí názvu oboru&#45;bloku") <br/>
Rozsah bloku a skrytí názvu

Výstup z programu zobrazeného na obrázku je:

```cpp
i = 0
i = 7
j = 9
i = 0
```

> [!NOTE]
> Argument `szWhat` je považován za argument nacházející se v oboru funkce. Proto je zpracováván stejně, jako by byl deklarován v nejvzdálenějším bloku funkce.

## <a name="hiding-class-names"></a>Skrytí názvů tříd

Názvy tříd lze skrýt deklarováním funkce, objektu, proměnné nebo enumerátoru ve stejném oboru. K názvu třídy je však stále možné přihlašovat, pokud je uvozena klíčovým slovem **Class**.

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

    cout << "Opening account with a balance of: "
         << Checking.GetBalance() << "\n";
}
//Output: Opening account with a balance of: 15.37
```

> [!NOTE]
> Jakékoli místo `Account` , pro které je volána třída Name (), klíčová slova musí být použita k odlišení od účtu proměnné s globálním rozsahem. Toto pravidlo neplatí, vyskytne-li se název třídy na levé straně operátoru rozlišení oboru (::). Názvy na levé straně operátoru rozlišení oboru jsou vždy považovány za názvy tříd.

Následující příklad ukazuje, jak deklarovat ukazatel na objekt typu `Account` pomocí klíčového slova **Class** :

```cpp
class Account *Checking = new class Account( Account );
```

`Account`V inicializátoru (v závorkách) v předchozím příkazu má globální rozsah, je typu **Double**.

> [!NOTE]
> Opětovné použití názvů identifikátorů, jak je znázorněno v tomto příkladu, je považováno za špatný styl programování.

Informace o deklaraci a inicializaci objektů třídy naleznete v tématu [třídy, struktury a sjednocení](../cpp/classes-and-structs-cpp.md). Informace o použití operátorů **New** a **Delete** volného obchodu najdete v tématu [operátory New a DELETE](new-and-delete-operators.md).

## <a name="hiding-names-with-global-scope"></a>Skrytí názvů s globálním rozsahem

Názvy s globálním rozsahem můžete skrýt explicitní deklarací stejného názvu v oboru bloku. K názvům globálního oboru však lze přistupovat pomocí operátoru rozlišení oboru ( `::` ).

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
