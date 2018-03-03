---
title: Rozsah (Visual C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 55baa4496522336a5a64ee81daa7a8ce484534c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="scope-visual-c"></a>Rozsah (Visual C++)
Názvy v jazyce C++ lze použít pouze v určité oblasti programu. Tato oblast se nazývá "obor" název. Obor určuje "životnost" název, který neoznačuje objekt statický rozsah. Obor rovněž určuje, zda název, pokud se označují jako třída konstruktory a destruktory a pokud jsou inicializovány proměnné místní do oboru. (Další informace najdete v tématu [konstruktory](../cpp/constructors-cpp.md) a [destruktory](../cpp/destructors-cpp.md).) Jsou k dispozici pět typy oboru:  
  
-   **Místní rozsah** název deklarované v rámci bloku je přístupné pouze v rámci tohoto bloku a bloky uzavřené tímto a až po bod deklarace. Názvy formální argumenty funkce v oboru bloku nejkrajnější funkce mít místní oboru, jako kdyby byla deklarována uvnitř bloku obklopuje tělo funkce. Předpokládejme následující fragment kódu:  
  
    ```  
    {  
        int i;  
    }  
    ```  
  
     Protože deklaraci `i` je v bloku uzavřené do složených závorek `i` má místní rozsah a je nikdy přístupný, protože žádný kód přistupuje k ho před uzavírací složených závorek.  
  
-   **Funkce oboru** popisky jsou pouze názvy, které mají rozsah funkce. Lze použít kdekoli v rámci funkce, ale nejsou přístupné mimo této funkce. Formální argumenty funkcí (argumenty zadané v definicích funkcí) jsou považovány za argumenty v rozsahu vnějšího bloku těla funkce.  
  
-   **Soubor oboru** libovolný název deklarovaný mimo všechny bloky nebo třídy má rozsah souboru. Je dostupné kdekoli v jednotce překlad po jeho deklaraci. Názvech s rozsahem souboru, které nedeklarujte statické objekty se často nazývají globální názvy.  
  
     V jazyce C++ rozsah souboru se také označuje jako obor názvů.  
  
-   **Třída oboru** názvy členů třídy mají rozsah třídy. Členské funkce třídy je přístupná jenom pomocí operátory výběru členů (**.** nebo  **->** ) nebo operátory ukazatelů na členy (**.\***  nebo  **-> \*** ) k objektu nebo ukazatele na objekt třídy; nestatické třída člen data považována za místní k objektu této třídy. Vezměte v úvahu následující deklaraci třídy:  
  
    ```  
    class Point  
    {  
        int x;  
        int y;  
    };  
    ```  
  
     Členy třídy `x` a `y` se považují za v oboru třídy `Point`.  
  
-   **Rozsah prototypu** názvy, které jsou deklarované v prototyp funkce jsou viditelné pouze až do konce prototypu. Následující prototyp deklaruje tři názvy (`strDestination`, `numberOfElements`, a `strSource`); tyto názvy se dostala mimo rozsah na konci prototyp:  
  
    ```  
    errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );  
    ```  
  
## <a name="hiding-names"></a>Skrytí názvů  
 Název lze skrýt jeho deklarací v uzavřeném bloku. Na následujícím obrázku je `i` deklarováno v rámci vnitřního bloku, a tím dojde ke skrytí proměnné přidružené k `i` v rozsahu vnějšího bloku.  
  
 ![Blok & č. 45; skrytí název oboru](../cpp/media/vc38sf1.png "vc38SF1")  
Rozsah bloku a skrytí názvu  
  
 Výstup z programu zobrazeného na obrázku je:  
  
```  
i = 0  
i = 7  
j = 9  
i = 0  
```  
  
> [!NOTE]
>  Argument `szWhat` je považován za argument nacházející se v oboru funkce. Proto je zpracováván stejně, jako by byl deklarován v nejvzdálenějším bloku funkce.  
  
## <a name="hiding-class-names"></a>Skrytí názvy tříd  
 Názvy tříd lze skrýt deklarováním funkce, objektu, proměnné nebo enumerátoru ve stejném oboru. Ale název třídy můžete v případě dál dostat předponu klíčové slovo **třída**.  
  
```  
// hiding_class_names.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
// Declare class Account at file scope.  
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
>  U jakéhokoli místa, ze kterého je volán název třídy (`Account`), je třeba použít klíčové slovo class pro odlišení od proměnné s rozsahem souboru Account. Toto pravidlo neplatí, vyskytne-li se název třídy na levé straně operátoru rozlišení oboru (::). Názvy na levé straně operátoru rozlišení oboru jsou vždy považovány za názvy tříd.  
  
 Následující příklad ukazuje, jak deklarovat ukazatel na objekt typu `Account` pomocí **třída** – klíčové slovo:  
  
```  
class Account *Checking = new class Account( Account );  
```  
  
 `Account` v inicializátoru (v závorkách) v předchozím příkazu je rozsah souboru; je typu **dvojité**.  
  
> [!NOTE]
>  Opětovné použití názvů identifikátorů, jak je znázorněno v tomto příkladu, je považováno za špatný styl programování.  
  
 Další informace o ukazatelích najdete v tématu [odvozené typy](http://msdn.microsoft.com/en-us/aa14183c-02fe-4d81-95fe-beddb0c01c7c). Informace o deklarace a inicializace třídy objektů najdete v tématu [tříd, struktur a sjednocení](../cpp/classes-and-structs-cpp.md). Informace o používání **nové** a **odstranit** bez úložiště operátory najdete v tématu [nové a odstraňte operátory](new-and-delete-operators.md).  
  
## <a name="hiding-names-with-file-scope"></a>Skrytí názvech s rozsahem souboru  
 Názvy s rozsahem souboru lze skrýt pomocí explicitní deklarace stejného názvu v rozsahu bloku. Avšak k názvům v rozsahu souboru lze přistupovat pomocí operátoru rozlišení oboru (`::`).  
  
```  
// file_scopes.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int i = 7;   // i has file scope, outside all blocks  
using namespace std;  
  
int main( int argc, char *argv[] ) {  
   int i = 5;   // i has block scope, hides i at file scope  
   cout << "Block-scoped i has the value: " << i << "\n";  
   cout << "File-scoped i has the value: " << ::i << "\n";  
}  
```  
  
```Output  
Block-scoped i has the value: 5  
File-scoped i has the value: 7  
```  
  
## <a name="see-also"></a>Viz také  
 [Základní koncepty](../cpp/basic-concepts-cpp.md)