---
title: 'Postupy: Vytvoření a používání instancí ukazatelů shared_ptr'
ms.custom: how-to
ms.date: 05/22/2019
ms.topic: conceptual
ms.assetid: 7d6ebb73-fa0d-4b0b-a528-bf05de96518e
ms.openlocfilehash: ac6db74122383ef8adb0f208860a6f6fba02dcc7
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821692"
---
# <a name="how-to-create-and-use-sharedptr-instances"></a>Postupy: Vytvoření a používání instancí ukazatelů shared_ptr

Typ `shared_ptr` je inteligentní ukazatel ve standardní knihovně jazyka C++ určený pro scénáře, ve kterých musí více než jeden vlastník spravovat dobu života objektu v paměti. Po inicializaci typu `shared_ptr` jej lze zkopírovat, předat hodnotou argumentům funkce nebo přiřadit dalším instancím typu `shared_ptr`. Všechny tyto instance ukazují na stejný objekt a sdílejí přístup k jednomu „řídicímu bloku“, který zvyšuje a snižuje počet odkazů, kdykoli je nová instance typu `shared_ptr` přidána, dostane se mimo rozsah nebo je obnovena. Když počet odkazů dosáhne nuly, řídicí blok odstraní prostředky paměti a sám sebe.

Následující obrázek znázorňuje několik instancí typu `shared_ptr`, které odkazují na jedno umístění v paměti.

![Sdílený ukazatel diagram](../cpp/media/shared_ptr.png "diagram sdílený ukazatel")

## <a name="example-setup"></a>Příklad nastavení

Příklady, které následují všechny Předpokládejme, že jste zahrnout požadované záhlaví a deklarovat požadované typy, jak je znázorněno zde:

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

Kdykoli je to možné, použijte [make_shared](../standard-library/memory-functions.md#make_shared) funkci, která vytvoří `shared_ptr` kdy je prostředek paměti vytvořen poprvé. Funkce `make_shared` zaručuje bezpečnost výjimek. Používá stejné volání pro přidělení paměti řídicímu bloku a prostředku, což snižuje zatížení při jejich konstrukci. Pokud nepoužíváte `make_shared`, pak je nutné použít explicitní `new` výrazu k vytvoření objektu před jeho předáním `shared_ptr` konstruktoru. Následující příklad ukazuje různé způsoby deklarace a inicializace instancí typu `shared_ptr` společně s novým objektem.

[!code-cpp[stl_smart_pointers#1](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_1.cpp)]

## <a name="example-2"></a>Příklad 2

Následující příklad ukazuje deklaraci a inicializaci instancí typu `shared_ptr`, jež převezmou sdílené vlastnictví objektu, který již byl vytvořen jinou instancí typu `shared_ptr`. Předpokládejme, že proměnná `sp2` je inicializována instancí typu `shared_ptr`.

[!code-cpp[stl_smart_pointers#2](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_2.cpp)]

## <a name="example-3"></a>Příklad 3

`shared_ptr` je také užitečný v C++ kontejnery standardní knihovny, při použití algoritmů, které kopírují prvky. Prvky lze zabalit do instance typu `shared_ptr` a poté je zkopírovat do jiných kontejnerů s vědomím, že základní paměť je platná tak dlouho, dokud ji potřebujete a ne déle. Následující příklad ukazuje, jak použít algoritmus `replace_copy_if` s instancemi typu `shared_ptr` v instanci typu vector.

[!code-cpp[stl_smart_pointers#4](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_3.cpp)]

## <a name="example-4"></a>Příklad 4:

K přetypování instance typu `dynamic_pointer_cast` lze použít funkce `static_pointer_cast`, `const_pointer_cast` a `shared_ptr`. Tyto funkce se podobají operátorům `dynamic_cast`, `static_cast` a `const_cast`. Následující příklad ukazuje, jak otestovat odvozený typ základních tříd každého prvku vektoru instancí typu `shared_ptr` a poté tyto prvky zkopírovat a zobrazit o nich informace.

[!code-cpp[stl_smart_pointers#5](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_4.cpp)]

## <a name="example-5"></a>Příklad 5

Instanci typu `shared_ptr` lze předat jiné funkci následujícími způsoby:

- Předání instance typu `shared_ptr` hodnotou. To zavolá kopii konstruktoru, zvýší počet odkazů a volaného učiní vlastníkem. Existuje malé množství režie při této operaci, což může být významné v závislosti na tom, kolik `shared_ptr` při předávání objektů. Tuto možnost použijte, pokud implicitní nebo explicitní kontrakt mezi volajícím a volaným vyžaduje, aby volaný byl vlastníkem.

- Předání instance typu `shared_ptr` odkazem nebo konstantním odkazem. V takovém případě není počet odkazů zvýšen a volaný může přistupovat k ukazatele, pokud volající nemá dostanou mimo rozsah. Nebo volaný může rozhodnout o vytvoření `shared_ptr` založeném na tomto odkazu a stát sdíleným vlastníkem. Tuto možnost použijte, když volající nezná volaného nebo když je nutné předat instanci typu `shared_ptr` a chcete se vyhnout operaci kopírování z důvodů výkonu.

- Předání základního ukazatele nebo odkazu na základní objekt. To umožňuje volanému tento objekt použít, ale neumožňuje sdílení vlastnictví ani prodloužení doby života ho. Pokud volaný vytvoří `shared_ptr` z nezpracovaný ukazatel nové `shared_ptr` je nezávislá na původním a nemá pod kontrolou tento základní prostředek spravovat. Tuto možnost použijte, pokud kontrakt mezi volajícím a volaným jasně určuje, že volajícímu zůstane vlastnictví po dobu života instance typu `shared_ptr`.

- Pokud se rozhodujete, jak předat `shared_ptr`, určete, zda volaný musí sdílet vlastnictví základního prostředku. „Vlastník“ je objekt nebo funkce, která může základní prostředek zachovat naživu tak dlouho, dokud jej potřebuje. Pokud volající musí zaručit, že volaný může prodloužit dobu života ukazatele nad rámec své doby života (funkce), použijte první možnost. Pokud není důležité, zda volaný prodlouží dobu života, použijte předání odkazem a nechte volaného, aby je zkopíroval či nikoli.

- Pokud máte k udělení přístupu k pomocné funkce základního ukazatele, a vědět, že pomocnou funkci se právě použijete tento ukazatel a vrátí se před vrácením volající funkce vrátí tuto funkci a nemusí sdílet vlastnictví základního ukazatele. K tomuto ukazateli má přístup jen během doby života instance typu `shared_ptr` volajícího. V takovém případě je bezpečné předat instanci typu `shared_ptr` podle odkazem nebo předat obyčejný ukazatel nebo odkaz na základní objekt. Předání tímto způsobem mírně zlepšuje výkon a může také pomoci lépe vyjádřit záměr programu.

- Někdy, například pro typ `std::vector<shared_ptr<T>>`, bude pravděpodobně nutné předat každou instanci typu `shared_ptr` tělu výrazu lambda nebo objektu pojmenované funkce. Pokud výraz lambda nebo funkce ukazatel neukládá, předejte `shared_ptr` odkazem, abyste zabránili volání kopie konstruktoru pro každý prvek.

## <a name="example-6"></a>Příklad 6

Následující příklad ukazuje, jak typ `shared_ptr` přetěžuje různé operátory porovnání, což umožňuje porovnání ukazatelů na paměť, která je vlastněna instancemi typu `shared_ptr`.

[!code-cpp[stl_smart_pointers#3](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_6.cpp)]

## <a name="see-also"></a>Viz také:

[Chytré ukazatele (moderní verze jazyka C++)](../cpp/smart-pointers-modern-cpp.md)
