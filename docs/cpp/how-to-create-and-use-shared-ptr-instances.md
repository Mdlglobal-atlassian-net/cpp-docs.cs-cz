---
title: 'Postupy: Vytvoření a používání instancí ukazatelů shared_ptr'
ms.custom: how-to
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 7d6ebb73-fa0d-4b0b-a528-bf05de96518e
ms.openlocfilehash: 8363139efddb2fa64057fdb995ab7bd5dfbcfd9b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153743"
---
# <a name="how-to-create-and-use-sharedptr-instances"></a>Postupy: Vytvoření a používání instancí ukazatelů shared_ptr

Typ `shared_ptr` je inteligentní ukazatel ve standardní knihovně jazyka C++ určený pro scénáře, ve kterých musí více než jeden vlastník spravovat dobu života objektu v paměti. Po inicializaci typu `shared_ptr` jej lze zkopírovat, předat hodnotou argumentům funkce nebo přiřadit dalším instancím typu `shared_ptr`. Všechny tyto instance ukazují na stejný objekt a sdílejí přístup k jednomu „řídicímu bloku“, který zvyšuje a snižuje počet odkazů, kdykoli je nová instance typu `shared_ptr` přidána, dostane se mimo rozsah nebo je obnovena. Když počet odkazů dosáhne nuly, řídicí blok odstraní prostředky paměti a sám sebe.

Následující obrázek znázorňuje několik instancí typu `shared_ptr`, které odkazují na jedno umístění v paměti.

![Sdílený ukazatel diagram](../cpp/media/shared_ptr.png "diagram sdílený ukazatel")

## <a name="example-1"></a>Příklad 1

Kdykoli je to možné, použijte [make_shared](../standard-library/memory-functions.md#make_shared) funkci, která vytvoří `shared_ptr` kdy je prostředek paměti vytvořen poprvé. Funkce `make_shared` zaručuje bezpečnost výjimek. Používá stejné volání pro přidělení paměti řídicímu bloku a prostředku a tím snižuje zatížení při jejich konstrukci. Pokud funkci `make_shared` nepoužijete, je pro vytvoření objektu před jeho předáním konstruktoru typu `shared_ptr` nutné použít explicitní nový výraz. Následující příklad ukazuje různé způsoby deklarace a inicializace instancí typu `shared_ptr` společně s novým objektem.

[!code-cpp[stl_smart_pointers#1](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_1.cpp)]

## <a name="example-2"></a>Příklad 2

Následující příklad ukazuje deklaraci a inicializaci instancí typu `shared_ptr`, jež převezmou sdílené vlastnictví objektu, který již byl vytvořen jinou instancí typu `shared_ptr`. Předpokládejme, že proměnná `sp2` je inicializována instancí typu `shared_ptr`.

[!code-cpp[stl_smart_pointers#2](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_2.cpp)]

## <a name="example-3"></a>Příklad 3

`shared_ptr` je také užitečný v kontejnery standardní knihovny C++ při použití algoritmů, které kopírují prvky. Prvky lze zabalit do instance typu `shared_ptr` a poté je zkopírovat do jiných kontejnerů s vědomím, že základní paměť je platná tak dlouho, dokud ji potřebujete a ne déle. Následující příklad ukazuje, jak použít algoritmus `replace_copy_if` s instancemi typu `shared_ptr` v instanci typu vector.

[!code-cpp[stl_smart_pointers#4](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_3.cpp)]

## <a name="example-4"></a>Příklad 4:

K přetypování instance typu `dynamic_pointer_cast` lze použít funkce `static_pointer_cast`, `const_pointer_cast` a `shared_ptr`. Tyto funkce se podobají operátorům `dynamic_cast`, `static_cast` a `const_cast`. Následující příklad ukazuje, jak otestovat odvozený typ základních tříd každého prvku vektoru instancí typu `shared_ptr` a poté tyto prvky zkopírovat a zobrazit o nich informace.

[!code-cpp[stl_smart_pointers#5](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_4.cpp)]

## <a name="example-5"></a>Příklad 5

Instanci typu `shared_ptr` lze předat jiné funkci následujícími způsoby:

- Předání instance typu `shared_ptr` hodnotou. To zavolá kopii konstruktoru, zvýší počet odkazů a volaného učiní vlastníkem. Tato operace představuje malé množství režie, což může být významné v závislosti na tom, kolik objektů `shared_ptr` předáváte. Tuto možnost použijte, pokud kontrakt (implicitní nebo explicitní) mezi volajícím a volaným vyžaduje, aby volaný byl vlastníkem.

- Předání instance typu `shared_ptr` odkazem nebo konstantním odkazem. V tomto případě není počet odkazů zvýšen a volaný má k ukazateli přístup, dokud se volající nedostane mimo rozsah. Nebo volaný může rozhodnout o vytvoření objektu `shared_ptr` založeném na tomto odkazu a tím se stát sdíleným vlastníkem. Tuto možnost použijte, když volající nezná volaného nebo když je nutné předat instanci typu `shared_ptr` a chcete se vyhnout operaci kopírování z důvodů výkonu.

- Předání základního ukazatele nebo odkazu na základní objekt. Umožňuje volanému tento objekt použít, ale neumožňuje sdílení vlastnictví ani prodloužení doby života. Pokud volaný vytvoří instanci typu `shared_ptr` z obyčejného ukazatele, tato nová instance typu `shared_ptr` bude nezávislá na původním ukazateli a nebude tento základní prostředek spravovat. Tuto možnost použijte, pokud kontrakt mezi volajícím a volaným jasně určuje, že volajícímu zůstane vlastnictví po dobu života instance typu `shared_ptr`.

- Pokud se rozhodujete, jak předat instanci typu `shared_ptr`, zjistěte, zda volaný musí sdílet vlastnictví základního prostředku. „Vlastník“ je objekt nebo funkce, která může základní prostředek zachovat naživu tak dlouho, dokud jej potřebuje. Pokud volající musí zaručit, že volaný může prodloužit dobu života ukazatele nad rámec své doby života (funkce), použijte první možnost. Pokud není důležité, zda volaný prodlouží dobu života, použijte předání odkazem a nechte volaného, aby je zkopíroval či nikoli.

- Pokud potřebujete pomocné funkci udělit přístup k základnímu ukazateli a víte, že tento ukazatel pouze použije a vrátí se před vrácením volající funkce, tato funkce nemusí sdílet vlastnictví základního ukazatele. K tomuto ukazateli má přístup jen během doby života instance typu `shared_ptr` volajícího. V tomto případě je bezpečné předat instanci typu `shared_ptr` odkazem nebo předat obyčejný ukazatel nebo odkaz na základní objekt. Předání tímto způsobem mírně zlepšuje výkon a může také pomoci lépe vyjádřit záměr programu.

- Někdy, například pro typ `std:vector<shared_ptr<T>>`, bude pravděpodobně nutné předat každou instanci typu `shared_ptr` tělu výrazu lambda nebo objektu pojmenované funkce. Pokud výraz lambda nebo funkce tento ukazatel neukládá, předejte instanci typu `shared_ptr` odkazem, abyste zabránili volání kopie konstruktoru pro každý prvek.

## <a name="example-6"></a>Příklad 6

Následující příklad ukazuje, jak typ `shared_ptr` přetěžuje různé operátory porovnání, což umožňuje porovnání ukazatelů na paměť, která je vlastněna instancemi typu `shared_ptr`.

[!code-cpp[stl_smart_pointers#3](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_6.cpp)]

## <a name="see-also"></a>Viz také:

[Chytré ukazatele (moderní verze jazyka C++)](../cpp/smart-pointers-modern-cpp.md)
