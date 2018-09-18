---
title: 'Deklarátor odkazu lvalue: &amp; | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '&'
dev_langs:
- C++
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28e5d247c866247b42da8937894fed878985be44
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090078"
---
# <a name="lvalue-reference-declarator-amp"></a>Deklarátor odkazu lvalue: &amp;

Uchovává adresu objektu, ale chová se syntakticky stejně jako objekt.

## <a name="syntax"></a>Syntaxe

```
type-id & cast-expression
```

## <a name="remarks"></a>Poznámky

Odkaz l-hodnoty si lze představit jako jiný název objektu. Deklarace odkazu l-hodnoty se skládá z volitelného seznamu specifikátorů, který je následován deklarátorem odkazu. Odkaz musí být inicializován a nelze jej změnit.

Libovolný objekt, jehož adresu lze převést na daný typ ukazatele, lze převést na podobný typ odkazu. Například každý objekt, jehož adresu lze převést na typ `char *`, lze také převést na typ `char &`.

Nepleťte si deklaraci odkazu s využitím [operátoru address-of](../cpp/address-of-operator-amp.md). Když `&` *identifikátor* předcházena typem, jako například **int** nebo **char**, *identifikátor* je deklarován jako odkaz na typ. Když `&` *identifikátor* párový příkaz není typem, využití představuje z operátoru address-of.

## <a name="example"></a>Příklad

Následující příklad ukazuje deklarátor odkazu deklarováním objektu `Person` a odkazu na tento objekt. Vzhledem k tomu, že `rFriend` je odkazem na `myFriend`, úprava proměnné změní stejný objekt.

```cpp
// reference_declarator.cpp
// compile with: /EHsc
// Demonstrates the reference declarator.
#include <iostream>
using namespace std;

struct Person
{
    char* Name;
    short Age;
};

int main()
{
   // Declare a Person object.
   Person myFriend;

   // Declare a reference to the Person object.
   Person& rFriend = myFriend;

   // Set the fields of the Person object.
   // Updating either variable changes the same object.
   myFriend.Name = "Bill";
   rFriend.Age = 40;

   // Print the fields of the Person object to the console.
   cout << rFriend.Name << " is " << myFriend.Age << endl;
}
```

```Output
Bill is 40
```

## <a name="see-also"></a>Viz také:

[Odkazy](../cpp/references-cpp.md)<br/>
[Argumenty funkce typu odkazu](../cpp/reference-type-function-arguments.md)<br/>
[Funkce vracející typ odkazu](../cpp/reference-type-function-returns.md)<br/>
[Odkazy na ukazatele](../cpp/references-to-pointers.md)