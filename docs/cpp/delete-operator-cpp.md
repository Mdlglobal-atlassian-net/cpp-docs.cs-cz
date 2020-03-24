---
title: delete – operátor (C++)
ms.date: 08/12/2019
f1_keywords:
- delete_cpp
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
ms.openlocfilehash: 2ffb307aa3eb6bb8d253129a550c95342ad497bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189465"
---
# <a name="delete-operator-c"></a>delete – operátor (C++)

Zruší přidělení bloku paměti.

## <a name="syntax"></a>Syntaxe

> [`::`] `delete` *cast-expression*\
> [`::`] `delete []` *přetypování – výraz*

## <a name="remarks"></a>Poznámky

Argument *cast-expression* musí být ukazatel na blok paměti dříve přidělený pro objekt vytvořený pomocí [operátoru new](../cpp/new-operator-cpp.md). Operátor **Delete** má výsledek typu **void** , a proto nevrací hodnotu. Příklad:

```cpp
CDialog* MyDialog = new CDialog;
// use MyDialog
delete MyDialog;
```

Použití **Delete** u ukazatele na objekt, který není přidělen s **novými** , poskytuje nepředvídatelné výsledky. Můžete však použít příkaz **Odstranit** na ukazatel s hodnotou 0. Toto zřízení znamená, že když **Nový** vrátí hodnotu 0 při selhání, odstraní se výsledek neúspěšné **nové** operace, která je neškodná. Další informace najdete v tématu [operátory New a DELETE](../cpp/new-and-delete-operators.md).

Operátory **New** a **Delete** lze použít také pro předdefinované typy, včetně polí. Pokud `pointer` odkazuje na pole, před `pointer`vložte prázdné hranaté závorky (`[]`):

```cpp
int* set = new int[100];
//use set[]
delete [] set;
```

Použití operátoru **Delete** u objektu zruší přidělení paměti. Program, který přistoupí přes ukazatel po odstranění objektu, může mít nepředvídatelné výsledky nebo se zhroutit.

Je-li pro **zrušení** přidělení paměti objektu C++ třídy použit příkaz DELETE, je před uvolněním paměti objektu volán destruktor objektu (Pokud objekt má destruktor).

Pokud je operandem operátoru **Delete** upravitelná l-hodnota, její hodnota není definována po odstranění objektu.

Pokud je zadána možnost kompilátoru [/SDL (povolit další kontroly zabezpečení)](/cpp/build/reference/sdl-enable-additional-security-checks) , je Operand operátoru **Delete** po odstranění objektu nastaven na neplatnou hodnotu.

## <a name="using-delete"></a>Používání příkazu delete

Existují dvě syntaktické varianty pro [operátor delete](../cpp/delete-operator-cpp.md): jeden pro jednotlivé objekty a druhý pro pole objektů. Následující fragment kódu ukazuje, jak se liší:

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

V následujících dvou případech jsou vyprodukovány nedefinované výsledky: použití pole pro odstranění (`delete []`) na objekt a použití formuláře bez pole DELETE v poli.

## <a name="example"></a>Příklad

Příklady použití **Delete**naleznete v tématu [New operator](../cpp/new-operator-cpp.md).

## <a name="how-delete-works"></a>Jak funguje odstranění

Operátor delete vyvolá **operátor funkce Delete**.

Pro objekty, které nejsou typu třídy ([Třída](../cpp/class-cpp.md), [Struktura](../cpp/struct-cpp.md)nebo [sjednocení](../cpp/unions.md)), je vyvolán globální operátor delete. V případě objektů typu třídy je název funkce zrušení přidělení vyřešen v globálním oboru, pokud výraz DELETE začíná operátorem rozlišení oboru (`::`). V opačném případě operátor delete vyvolá destruktor objektu před zrušením přidělení paměti (pokud není ukazatel null). Operátor delete lze definovat na základě každé třídy. Neexistuje-li pro zadanou třídu žádná taková definice, je vyvolán globální operátor delete. Je-li výraz delete používán k zrušení přidělení objektu třídy, jehož statický typ má virtuální destruktor, je funkce zrušení přidělení řešena prostřednictvím virtuálního konstruktoru dynamického typu objektu.

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)\
\ [klíčových slov](../cpp/keywords-cpp.md)
[Operátory new a delete](../cpp/new-and-delete-operators.md)
