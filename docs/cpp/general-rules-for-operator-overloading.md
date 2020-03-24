---
title: Obecná pravidla přetížení operátoru
ms.date: 11/04/2016
helpviewer_keywords:
- operator overloading [C++], rules
ms.assetid: eb2b3754-35f7-4832-b1da-c502893dc0c7
ms.openlocfilehash: 0c8cbea3411acd50be376ae0853a143af57458f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188587"
---
# <a name="general-rules-for-operator-overloading"></a>Obecná pravidla přetížení operátoru

Následující pravidla omezují způsob, jakým jsou implementovány přetížené operátory. Neplatí však pro operátory [New](../cpp/new-operator-cpp.md) a [Delete](../cpp/delete-operator-cpp.md) , které jsou pokryty samostatně.

- Nelze definovat nové operátory, jako například **.** .

- Nelze předefinovat význam operátorů při použití předdefinovaných datových typů.

- Přetížené operátory musejí být členskými funkcemi nestatické třídy nebo globálními funkcemi. Globální funkce, která požaduje přístup k soukromým nebo chráněným členům, musí být pro danou třídu deklarována jako přátelská. Globální funkce musí přebírat alespoň jeden argument třídy nebo výčtového typu, případně odkazu na třídu nebo výčtový typ. Příklad:

    ```cpp
    // rules_for_operator_overloading.cpp
    class Point
    {
    public:
        Point operator<( Point & );  // Declare a member operator
                                     //  overload.
        // Declare addition operators.
        friend Point operator+( Point&, int );
        friend Point operator+( int, Point& );
    };

    int main()
    {
    }
    ```

   Předchozí příklad kódu deklaruje operátor „menší než“ jako členskou funkci. Operátory sčítání jsou však deklarovány jako globální funkce, které mají „přátelský“ přístup. Pro daný operátor může být poskytnuta více než jedna implementace. V případě předchozího operátoru sčítání jsou poskytnuty dvě implementace pro poskytnutí komutativity. Je tak pravděpodobné, že operátory, které přidávají `Point` do `Point`, **int** do `Point`a tak dále, mohou být implementovány.

- Operátory dodržují seskupování a respektují počet operandů zadaný jejich typickým použitím v rámci předdefinovaných typů. Proto neexistuje žádný způsob, jak vyjádřit koncept "Add 2 a 3" objektu typu `Point`, "očekává se 2 Přidání na souřadnici *x* a 3 pro přidání do souřadnic *y* .

- Unární operátory, které jsou deklarovány jako členské funkce, nepřebírají žádné argumenty. Jsou-li deklarovány jako globální funkce, přebírají jeden argument.

- Binární operátory, které jsou deklarovány jako členské funkce, přebírají jeden argument. Jsou-li deklarovány jako globální funkce, přebírají dva argumenty.

- Pokud operátor lze použít jako unární nebo binární operátor ( __&__ , __*__ , __+__ a __-__ ), můžete každé použití přetížit samostatně.

- Přetížené operátory nemohou mít výchozí argumenty.

- Všechny přetížené operátory s výjimkou přiřazení (**operátor =** ) jsou děděny odvozenými třídami.

- První argument přetížených operátorů členské funkce je vždy typu třídy objektu, pro který je operátor vyvolán (třída, ve které je operátor deklarován nebo třída odvozená z této třídy). Pro první argument nejsou k dispozici žádné převody.

Význam libovolného operátoru lze zcela změnit. Který zahrnuje význam adres ( **&** ), přiřazení ( **=** ) a operátorů volání funkce. Identity, které lze dovolávat pro vestavěné typy, lze také změnit pomocí přetěžování operátoru. Následující čtyři příkazy jsou obvykle při vyhodnocování zcela ekvivalentní:

```cpp
var = var + 1;
var += 1;
var++;
++var;
```

Tuto identitu nelze dovolávat pro typy tříd, které přetěžují operátory. Kromě toho některé požadavky zahrnují použití těchto operátorů pro základní typy, které jsou zmírněny pro přetížené operátory. Například operátor sčítání a přiřazování **+=** vyžaduje, aby levý operand byl l-hodnotou při použití na základní typy; žádný takový požadavek neexistuje, pokud je operátor přetížený.

> [!NOTE]
> V rámci konzistence je při definování přetížených operátorů často nejlepší postupovat podle modelu předdefinovaných typů. Liší-li se významně sémantika přetíženého operátoru od jeho významu v jiných kontextech, může být více matoucí než užitečný.

## <a name="see-also"></a>Viz také

[Přetížení operátoru](../cpp/operator-overloading.md)
