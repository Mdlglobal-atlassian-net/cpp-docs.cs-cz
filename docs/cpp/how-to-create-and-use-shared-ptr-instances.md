---
title: 'Postupy: vytváření a používání instancí shared_ptr'
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
# <a name="how-to-create-and-use-shared_ptr-instances"></a>Postupy: vytváření a používání instancí shared_ptr

Typ `shared_ptr` je inteligentní ukazatel ve standardní knihovně jazyka C++ určený pro scénáře, ve kterých musí více než jeden vlastník spravovat dobu života objektu v paměti. Po inicializaci typu `shared_ptr` jej lze zkopírovat, předat hodnotou argumentům funkce nebo přiřadit dalším instancím typu `shared_ptr`. Všechny tyto instance ukazují na stejný objekt a sdílejí přístup k jednomu „řídicímu bloku“, který zvyšuje a snižuje počet odkazů, kdykoli je nová instance typu `shared_ptr` přidána, dostane se mimo rozsah nebo je obnovena. Když počet odkazů dosáhne nuly, řídicí blok odstraní prostředky paměti a sám sebe.

Následující obrázek znázorňuje několik instancí typu `shared_ptr`, které odkazují na jedno umístění v paměti.

![Sdílený diagram ukazatelů](media/shared_ptr.png "Sdílený diagram ukazatelů")

## <a name="example-setup"></a>Příklad nastavení

Následující příklady předpokládají, že jste zahrnuli požadované hlavičky a deklarovali požadované typy, jak je znázorněno zde:

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

Kdykoli je to možné, použijte funkci [make_shared](../standard-library/memory-functions.md#make_shared) k vytvoření `shared_ptr` při prvním vytvoření prostředku paměti. `make_shared` je bezpečný pro výjimky. Používá stejné volání k přidělení paměti řídicímu bloku a prostředku, což snižuje režii konstrukce. Pokud nepoužíváte `make_shared`, je nutné použít explicitní výraz `new` pro vytvoření objektu před jeho předáním do konstruktoru `shared_ptr`. Následující příklad ukazuje různé způsoby deklarace a inicializace instancí typu `shared_ptr` společně s novým objektem.

[!code-cpp[stl_smart_pointers#1](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_1.cpp)]

## <a name="example-2"></a>Příklad 2

Následující příklad ukazuje deklaraci a inicializaci instancí typu `shared_ptr`, jež převezmou sdílené vlastnictví objektu, který již byl vytvořen jinou instancí typu `shared_ptr`. Předpokládejme, že proměnná `sp2` je inicializována instancí typu `shared_ptr`.

[!code-cpp[stl_smart_pointers#2](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_2.cpp)]

## <a name="example-3"></a>Příklad 3

`shared_ptr` je také užitečné v C++ kontejnerech knihovny Standard, pokud používáte algoritmy, které kopírují prvky. Prvky lze zabalit do instance typu `shared_ptr` a poté je zkopírovat do jiných kontejnerů s vědomím, že základní paměť je platná tak dlouho, dokud ji potřebujete a ne déle. Následující příklad ukazuje, jak použít algoritmus `remove_copy_if` s instancemi typu `shared_ptr` v instanci typu vector.

[!code-cpp[stl_smart_pointers#4](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_3.cpp)]

## <a name="example-4"></a>Příklad 4:

K přetypování instance typu `dynamic_pointer_cast` lze použít funkce `static_pointer_cast`, `const_pointer_cast` a `shared_ptr`. Tyto funkce se podobají operátorům `dynamic_cast`, `static_cast` a `const_cast`. Následující příklad ukazuje, jak otestovat odvozený typ základních tříd každého prvku vektoru instancí typu `shared_ptr` a poté tyto prvky zkopírovat a zobrazit o nich informace.

[!code-cpp[stl_smart_pointers#5](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_4.cpp)]

## <a name="example-5"></a>Příklad 5

Instanci typu `shared_ptr` lze předat jiné funkci následujícími způsoby:

- Předání instance typu `shared_ptr` hodnotou. To zavolá kopii konstruktoru, zvýší počet odkazů a volaného učiní vlastníkem. Tato operace je malým množstvím režie, což může být významné v závislosti na počtu `shared_ptr` objektů, které předáváte. Tuto možnost použijte, pokud implicitní nebo explicitní kontrakt kódu mezi volajícím a volaným vyžaduje, aby volaný byl vlastníkem.

- Předání instance typu `shared_ptr` odkazem nebo konstantním odkazem. V tomto případě není počet odkazů zvýšen a volaný má k ukazateli přístup, pokud se volající nepřesune do rozsahu. Nebo volaný se může rozhodnout vytvořit `shared_ptr` na základě odkazu a stane se sdíleným vlastníkem. Tuto možnost použijte, když volající nezná volaného nebo když je nutné předat instanci typu `shared_ptr` a chcete se vyhnout operaci kopírování z důvodů výkonu.

- Předání základního ukazatele nebo odkazu na základní objekt. To umožňuje, aby volaný objekt používal, ale nepovolil sdílení vlastnictví nebo prodloužení doby života. Pokud volaný vytvoří `shared_ptr` z nezpracovaného ukazatele, nová `shared_ptr` je nezávislá na původní a neřídí základní prostředek. Tuto možnost použijte, pokud kontrakt mezi volajícím a volaným jasně určuje, že volajícímu zůstane vlastnictví po dobu života instance typu `shared_ptr`.

- Když rozhodujete, jak předat `shared_ptr`, určete, zda volaný musí sdílet vlastnictví podkladového prostředku. „Vlastník“ je objekt nebo funkce, která může základní prostředek zachovat naživu tak dlouho, dokud jej potřebuje. Pokud volající musí zaručit, že volaný může prodloužit dobu života ukazatele nad rámec své doby života (funkce), použijte první možnost. Pokud není důležité, zda volaný prodlouží dobu života, použijte předání odkazem a nechte volaného, aby je zkopíroval či nikoli.

- Pokud je nutné poskytnout pomocnou funkci přístup k základnímu ukazateli a víte, že pomocná funkce bude pouze používat ukazatel a vracet před vrácením volání funkce, pak tato funkce nemusí sdílet vlastnictví základního ukazatele. K tomuto ukazateli má přístup jen během doby života instance typu `shared_ptr` volajícího. V tomto případě je bezpečné předat `shared_ptr` odkazem nebo předat nezpracovaný ukazatel nebo odkaz na základní objekt. Předání tímto způsobem mírně zlepšuje výkon a může také pomoci lépe vyjádřit záměr programu.

- Někdy, například pro typ `std::vector<shared_ptr<T>>`, bude pravděpodobně nutné předat každou instanci typu `shared_ptr` tělu výrazu lambda nebo objektu pojmenované funkce. Pokud výraz lambda nebo funkce neuloží ukazatel, předejte `shared_ptr` odkazem, aby nedošlo k vyvolání kopírovacího konstruktoru pro každý prvek.

## <a name="example-6"></a>Příklad 6

Následující příklad ukazuje, jak typ `shared_ptr` přetěžuje různé operátory porovnání, což umožňuje porovnání ukazatelů na paměť, která je vlastněna instancemi typu `shared_ptr`.

[!code-cpp[stl_smart_pointers#3](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_6.cpp)]

## <a name="see-also"></a>Viz také:

[Chytré ukazatele (moderní verze jazyka C++)](smart-pointers-modern-cpp.md)
