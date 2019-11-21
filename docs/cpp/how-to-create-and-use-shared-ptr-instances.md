---
title: 'How to: Create and use shared_ptr instances'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 7d6ebb73-fa0d-4b0b-a528-bf05de96518e
ms.openlocfilehash: 9820e4cd2d1b981d82760fc1cea4e07c85792177
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245833"
---
# <a name="how-to-create-and-use-shared_ptr-instances"></a>How to: Create and Use shared_ptr instances

Typ `shared_ptr` je inteligentní ukazatel ve standardní knihovně jazyka C++ určený pro scénáře, ve kterých musí více než jeden vlastník spravovat dobu života objektu v paměti. Po inicializaci typu `shared_ptr` jej lze zkopírovat, předat hodnotou argumentům funkce nebo přiřadit dalším instancím typu `shared_ptr`. Všechny tyto instance ukazují na stejný objekt a sdílejí přístup k jednomu „řídicímu bloku“, který zvyšuje a snižuje počet odkazů, kdykoli je nová instance typu `shared_ptr` přidána, dostane se mimo rozsah nebo je obnovena. Když počet odkazů dosáhne nuly, řídicí blok odstraní prostředky paměti a sám sebe.

Následující obrázek znázorňuje několik instancí typu `shared_ptr`, které odkazují na jedno umístění v paměti.

![Shared pointer diagram](media/shared_ptr.png "Shared pointer diagram")

## <a name="example-setup"></a>Example setup

The examples that follow all assume that you've included the required headers and declared the required types, as shown here:

```cpp
// shared_ptr-examples.cpp
// The following examples assume these declarations:
#include <algorithm>
#include <iostream>
#include <memory>
#include <string>
#include <vector>

struct MediaAsset
{
    virtual ~MediaAsset() = default; // make it polymorphic
};

struct Song : public MediaAsset
{
    std::wstring artist;
    std::wstring title;
    Song(const std::wstring& artist_, const std::wstring& title_) :
        artist{ artist_ }, title{ title_ } {}
};

struct Photo : public MediaAsset
{
    std::wstring date;
    std::wstring location;
    std::wstring subject;
    Photo(
        const std::wstring& date_,
        const std::wstring& location_,
        const std::wstring& subject_) :
        date{ date_ }, location{ location_ }, subject{ subject_ } {}
};

using namespace std;

int main()
{
    // The examples go here, in order:
    // Example 1
    // Example 2
    // Example 3
    // Example 4
    // Example 6
}
```

## <a name="example-1"></a>Příklad 1

Whenever possible, use the [make_shared](../standard-library/memory-functions.md#make_shared) function to create a `shared_ptr` when the memory resource is created for the first time. Funkce `make_shared` zaručuje bezpečnost výjimek. It uses the same call to allocate the memory for the control block and the resource, which reduces the construction overhead. If you don't use `make_shared`, then you have to use an explicit `new` expression to create the object before you pass it to the `shared_ptr` constructor. Následující příklad ukazuje různé způsoby deklarace a inicializace instancí typu `shared_ptr` společně s novým objektem.

[!code-cpp[stl_smart_pointers#1](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_1.cpp)]

## <a name="example-2"></a>Příklad 2

Následující příklad ukazuje deklaraci a inicializaci instancí typu `shared_ptr`, jež převezmou sdílené vlastnictví objektu, který již byl vytvořen jinou instancí typu `shared_ptr`. Předpokládejme, že proměnná `sp2` je inicializována instancí typu `shared_ptr`.

[!code-cpp[stl_smart_pointers#2](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_2.cpp)]

## <a name="example-3"></a>Příklad 3

`shared_ptr` is also helpful in C++ Standard Library containers when you're using algorithms that copy elements. Prvky lze zabalit do instance typu `shared_ptr` a poté je zkopírovat do jiných kontejnerů s vědomím, že základní paměť je platná tak dlouho, dokud ji potřebujete a ne déle. Následující příklad ukazuje, jak použít algoritmus `remove_copy_if` s instancemi typu `shared_ptr` v instanci typu vector.

[!code-cpp[stl_smart_pointers#4](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_3.cpp)]

## <a name="example-4"></a>Example 4

K přetypování instance typu `dynamic_pointer_cast` lze použít funkce `static_pointer_cast`, `const_pointer_cast` a `shared_ptr`. Tyto funkce se podobají operátorům `dynamic_cast`, `static_cast` a `const_cast`. Následující příklad ukazuje, jak otestovat odvozený typ základních tříd každého prvku vektoru instancí typu `shared_ptr` a poté tyto prvky zkopírovat a zobrazit o nich informace.

[!code-cpp[stl_smart_pointers#5](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_4.cpp)]

## <a name="example-5"></a>Example 5

Instanci typu `shared_ptr` lze předat jiné funkci následujícími způsoby:

- Předání instance typu `shared_ptr` hodnotou. To zavolá kopii konstruktoru, zvýší počet odkazů a volaného učiní vlastníkem. There's a small amount of overhead in this operation, which may be significant depending on how many `shared_ptr` objects you're passing. Use this option when the implied or explicit code contract between the caller and callee requires that the callee be an owner.

- Předání instance typu `shared_ptr` odkazem nebo konstantním odkazem. In this case, the reference count isn't incremented, and the callee can access the pointer as long as the caller doesn't go out of scope. Or, the callee can decide to create a `shared_ptr` based on the reference, and become a shared owner. Tuto možnost použijte, když volající nezná volaného nebo když je nutné předat instanci typu `shared_ptr` a chcete se vyhnout operaci kopírování z důvodů výkonu.

- Předání základního ukazatele nebo odkazu na základní objekt. This enables the callee to use the object, but doesn't enable it to share ownership or extend the lifetime. If the callee creates a `shared_ptr` from the raw pointer, the new `shared_ptr` is independent from the original, and doesn't control the underlying resource. Tuto možnost použijte, pokud kontrakt mezi volajícím a volaným jasně určuje, že volajícímu zůstane vlastnictví po dobu života instance typu `shared_ptr`.

- When you're deciding how to pass a `shared_ptr`, determine whether the callee has to share ownership of the underlying resource. „Vlastník“ je objekt nebo funkce, která může základní prostředek zachovat naživu tak dlouho, dokud jej potřebuje. Pokud volající musí zaručit, že volaný může prodloužit dobu života ukazatele nad rámec své doby života (funkce), použijte první možnost. Pokud není důležité, zda volaný prodlouží dobu života, použijte předání odkazem a nechte volaného, aby je zkopíroval či nikoli.

- If you have to give a helper function access to the underlying pointer, and you know that the helper function will just use the pointer and return before the calling function returns, then that function doesn't have to share ownership of the underlying pointer. K tomuto ukazateli má přístup jen během doby života instance typu `shared_ptr` volajícího. In this case, it's safe to pass the `shared_ptr` by reference, or pass the raw pointer or a reference to the underlying object. Předání tímto způsobem mírně zlepšuje výkon a může také pomoci lépe vyjádřit záměr programu.

- Někdy, například pro typ `std::vector<shared_ptr<T>>`, bude pravděpodobně nutné předat každou instanci typu `shared_ptr` tělu výrazu lambda nebo objektu pojmenované funkce. If the lambda or function doesn't store the pointer, then pass the `shared_ptr` by reference to avoid invoking the copy constructor for each element.

## <a name="example-6"></a>Example 6

Následující příklad ukazuje, jak typ `shared_ptr` přetěžuje různé operátory porovnání, což umožňuje porovnání ukazatelů na paměť, která je vlastněna instancemi typu `shared_ptr`.

[!code-cpp[stl_smart_pointers#3](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_6.cpp)]

## <a name="see-also"></a>Viz také:

[Chytré ukazatele (moderní verze jazyka C++)](smart-pointers-modern-cpp.md)
