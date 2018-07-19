---
title: Rozsah (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: e8af021120c06465d0fd79ead79e2a18cb593803
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027606"
---
# <a name="scope-c"></a>Rozsah (C++)

Při deklaraci elementu programu například třídy, funkce nebo proměnná, můžete jeho název pouze "Zobrazit" a používají v některých částech programu. Je volána kontext, ve kterém je viditelný název jeho *oboru*. Například, pokud deklarujete proměnnou `x` ve funkci, `x` je jenom viditelné v rámci této tělo funkce. Má *místní rozsah*. Ve svém programu; může mít jiné proměnné se stejným názvem tak dlouho, dokud jsou v různých oborech, že nebudou porušovat jednoho definičního pravidla a je vyvolána žádná chyba.

Pro automatické nestatické proměnné obor také určuje, kdy je vytvořeno a zničeno při v paměti pro programy. 

Existuje šest druhy rozsahů:

- **Globální rozsah** globální název je ten, který je deklarované mimo všechny třídy, funkce nebo oboru názvů. V jazyce C++ však i tyto názvy existovat implicitní globálního oboru názvů. Obor názvů globální sahá od deklarací na konec souboru, ve kterém jsou deklarovány. Pro globální názvy viditelnost také řídí pravidly [propojení](program-and-linkage-cpp.md) která určuje, zda je název zobrazen v jiných souborech v programu.

- **Obor Namespace** název, který je deklarován v rámci [obor názvů](namespaces-cpp.md), mimo všechny definice třídy nebo výčtu nebo blok funkce je viditelná z místa deklarace na konec objektu oboru názvů. Obor názvů může být definován ve více blocích přes různé soubory.

- **Místní rozsah** název deklarované v rámci funkce nebo lambda, včetně názvů parametrů mají místní rozsah. Jsou často označovány jako "místní". Jsou viditelné ze svého bodu deklarace na konec těla funkce nebo výrazu lambda. Místní rozsah je druh rozsahem bloku, která je popsána dále v tomto článku.

- **Třída oboru** názvy členů třídy mají obor třídy, která rozšiřuje v rámci definice třídy bez ohledu na to deklarací. Usnadnění přístupu člena třídy je další kontrolou **veřejné**, **privátní**, a **chráněné** klíčová slova. Veřejné nebo chráněné členy jsou přístupné pouze pomocí operátorů výběru členů (**.** nebo **->**) nebo operátory pointer-to-member (**.\***  nebo **-> \***).

- **Příkaz oboru** názvy deklarované v **pro**, **Pokud**, **při**, nebo **přepnout** příkazu jsou viditelné až do konce blok příkazů.

- **Funkce oboru** A [popisek](labeled-statements.md) má rozsah funkce, což znamená, že je viditelná ve tělo funkce ještě před jeho deklaraci. Rozsah funkce umožňuje psát příkazy, jako jsou `goto cleanup` před `cleanup` popisek je deklarován.

## <a name="hiding-names"></a>Skrytí názvů

Název lze skrýt jeho deklarací v uzavřeném bloku. Na následujícím obrázku je `i` deklarováno v rámci vnitřního bloku, a tím dojde ke skrytí proměnné přidružené k `i` v rozsahu vnějšího bloku.

 ![Blok&#45;oboru skrývání názvů](../cpp/media/vc38sf1.png "vc38SF1") rozsah bloku a skrytí názvu

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

 Názvy tříd lze skrýt deklarováním funkce, objektu, proměnné nebo enumerátoru ve stejném oboru. Ale název třídy i nadále přístupný při předponu klíčového slova **třídy**.

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
> Jakékoli místo názvu třídy (`Account`) je volána pro klíčové slovo class musí použije k odlišení od proměnné účtu pro globální obor. Toto pravidlo neplatí, vyskytne-li se název třídy na levé straně operátoru rozlišení oboru (::). Názvy na levé straně operátoru rozlišení oboru jsou vždy považovány za názvy tříd.

 Následující příklad ukazuje, jak deklarovat ukazatel na objekt typu `Account` pomocí **třídy** – klíčové slovo:

```cpp
class Account *Checking = new class Account( Account );
```

 `Account` v inicializátoru (v závorkách) v předchozím příkazu má globální obor; je typu **double**.

> [!NOTE]
> Opětovné použití názvů identifikátorů, jak je znázorněno v tomto příkladu, je považováno za špatný styl programování.

 Další informace o ukazatelích naleznete v tématu [odvozené typy](http://msdn.microsoft.com/aa14183c-02fe-4d81-95fe-beddb0c01c7c). Informace o deklaraci a inicializaci objektů tříd naleznete v tématu [třídy, struktury a sjednocení](../cpp/classes-and-structs-cpp.md). Informace o používání **nové** a **odstranit** operátorů volného úložiště najdete v tématu [nové a odstranit operátory](new-and-delete-operators.md).

## <a name="hiding-names-with-global-scope"></a>Skrytí názvů s globálním oboru

 Názvy s globálním rozsahem lze skrýt pomocí explicitní deklarace stejného názvu v oboru bloku. Ale globálního oboru názvů lze přistupovat pomocí operátoru rozlišení oboru (`::`).

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