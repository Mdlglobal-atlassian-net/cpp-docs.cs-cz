---
title: delete – operátor (C++)
ms.date: 11/04/2016
f1_keywords:
- delete_cpp
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
ms.openlocfilehash: 5e4f5685ea1bb8cd7c405373ba774fe36af08672
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524722"
---
# <a name="delete-operator-c"></a>delete – operátor (C++)

Zruší přidělení bloku paměti.

## <a name="syntax"></a>Syntaxe

```
[::] delete cast-expression
[::] delete [ ] cast-expression
```

## <a name="remarks"></a>Poznámky

*Výrazem přetypování* argument musí být ukazatelem na blok paměti dříve přidělené pro objekt vytvořený pomocí [operátor new](../cpp/new-operator-cpp.md). **Odstranit** operátor má výsledek typu **void** a proto nevrátí hodnotu. Příklad:

```cpp
CDialog* MyDialog = new CDialog;
// use MyDialog
delete MyDialog;
```

Pomocí **odstranit** na ukazatel na objekt nebyl přidělen pomocí **nové** poskytuje neočekávané výsledky. Můžete však použít **odstranit** na ukazatel s hodnotou 0. Toto zajištění znamená, že když **nové** vrátí hodnotu 0, při selhání, odstranění výsledku nezdařené **nové** operace je neškodný. V tématu [nové a odstranit operátory](../cpp/new-and-delete-operators.md) Další informace.

**Nové** a **odstranit** operátory lze také použít pro integrované typy, včetně polí. Pokud `pointer` odkazuje na pole, je třeba před `pointer` umístit prázdné závorky:

```cpp
int* set = new int[100];
//use set[]
delete [] set;
```

Použití **odstranit** operátor na objekt zruší přidělení paměti. Program, který přistoupí přes ukazatel po odstranění objektu, může mít nepředvídatelné výsledky nebo se zhroutit.

Když **odstranit** je používán k zrušení přidělení paměti pro objekt třídy jazyka C++, destruktor objektu je volána, před přidělení paměti objektu (Pokud má objekt destruktor).

Pokud operand **odstranit** operátor je upravitelná l hodnotou, její hodnota je po odstranění objektu nedefinovaná.

## <a name="using-delete"></a>Používání příkazu delete

Existují dvě syntaktické varianty pro [operátor delete](../cpp/delete-operator-cpp.md): jednu pro jednotlivé objekty a druhá pro pole objektů. Následující fragment kódu ukazuje, jak se liší:

```cpp
// expre_Using_delete.cpp
struct UDType
{
};

int main()
{
   // Allocate a user-defined object, UDObject, and an object
   //  of type double on the free store using the
   //  new operator.
   UDType *UDObject = new UDType;
   double *dObject = new double;
   // Delete the two objects.
   delete UDObject;
   delete dObject;
   // Allocate an array of user-defined objects on the
   // free store using the new operator.
   UDType (*UDArr)[7] = new UDType[5][7];
   // Use the array syntax to delete the array of objects.
   delete [] UDArr;
}
```

Následující dva případy vytvoří nedefinované výsledky: použitím operátoru delete (delete [ ]), který má podobu pole, na objekt a použitím operátoru delete, který nemá podobu pole, na pole.

## <a name="example"></a>Příklad

Příklady použití **odstranit**, naleznete v tématu [operátor new](../cpp/new-operator-cpp.md).

## <a name="how-delete-works"></a>Jak funguje výraz delete

Operátor delete vyvolá funkci **operátor delete**.

Pro objekty typu třídy ([třídy](../cpp/class-cpp.md), [struktura](../cpp/struct-cpp.md), nebo [sjednocení](../cpp/unions.md)), je vyvolán globální operátor delete. Začne-li výraz delete jednočlenným operátorem rozlišení rozsahu (::), název funkce navracení je pro objekty typu třídy řešen v globálním oboru. V opačném případě operátor delete vyvolá destruktor objektu před zrušením přidělení paměti (pokud není ukazatel null). Operátor delete lze definovat na základě každé třídy. Neexistuje-li pro zadanou třídu žádná taková definice, je vyvolán globální operátor delete. Je-li výraz delete používán k zrušení přidělení objektu třídy, jehož statický typ má virtuální destruktor, je funkce zrušení přidělení řešena prostřednictvím virtuálního konstruktoru dynamického typu objektu.

## <a name="see-also"></a>Viz také:

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Operátory new a delete](../cpp/new-and-delete-operators.md)