---
title: 'Postupy: vytváření a používání instancí unique_ptr'
ms.custom: how-to
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
ms.openlocfilehash: 4b3362f71d1ccab0efb03d7e8705c6b3f25f9780
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246526"
---
# <a name="how-to-create-and-use-unique_ptr-instances"></a>Postupy: vytváření a používání instancí unique_ptr

[Unique_ptr](../standard-library/unique-ptr-class.md) nesdílí svůj ukazatel. Nemůže být zkopírován do jiného `unique_ptr`, předáno hodnotou funkce nebo použit v jakémkoli C++ algoritmu standardní knihovny, který vyžaduje, aby byly provedeny kopie. `unique_ptr` lze přesunout pouze. To znamená, že vlastnictví prostředku paměti je převedeno do jiného `unique_ptr` a původní `unique_ptr` již nevlastní. Doporučujeme omezit objekt na jednoho vlastníka, protože více vlastnictví zkomplikuje programovou logiku. Proto pokud potřebujete inteligentní ukazatel pro prostý C++ objekt, použijte `unique_ptr`a při konstrukci `unique_ptr`použijte pomocnou funkci [make_unique](../standard-library/memory-functions.md#make_unique) .

Následující diagram znázorňuje přenos vlastnictví mezi dvěma instancemi `unique_ptr`.

![Přesunutí vlastnictví jedinečného&#95;PTR](media/unique_ptr.png "Přesunutí vlastnictví jedinečného&#95;PTR")

`unique_ptr` je definována v hlavičce `<memory>` ve C++ standardní knihovně. Je přesně tak efektivní jako nezpracovaný ukazatel a lze jej použít v C++ kontejnerech Standard Library. Přidání instancí `unique_ptr` do C++ kontejnerů standardních knihoven je efektivní, protože konstruktor přesunu `unique_ptr` eliminuje nutnost operace kopírování.

## <a name="example-1"></a>Příklad 1

Následující příklad ukazuje, jak vytvořit instance `unique_ptr` a předat je mezi funkcemi.

[!code-cpp[stl_smart_pointers#210](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]

Tyto příklady ukazují tuto základní charakteristiku `unique_ptr`: lze je přesunout, ale nikoli kopírovat. "Přesun" převede vlastnictví na novou `unique_ptr` a obnoví původní `unique_ptr`.

## <a name="example-2"></a>Příklad 2

Následující příklad ukazuje, jak vytvořit instance `unique_ptr` a používat je ve vektoru.

[!code-cpp[stl_smart_pointers#211](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]

V rozsahu smyčky si všimněte, že `unique_ptr` předává odkazem. Pokud se pokusíte předat hodnotu v tomto příkladu, kompilátor vyvolá chybu, protože je odstraněn konstruktor `unique_ptr` Copy.

## <a name="example-3"></a>Příklad 3

Následující příklad ukazuje, jak inicializovat `unique_ptr`, který je členem třídy.

[!code-cpp[stl_smart_pointers#212](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]

## <a name="example-4"></a>Příklad 4:

Můžete použít [make_unique](../standard-library/memory-functions.md#make_unique) k vytvoření `unique_ptr` pole, ale nelze použít `make_unique` k inicializaci prvků pole.

[!code-cpp[stl_smart_pointers#213](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]

Další příklady naleznete v tématu [make_unique](../standard-library/memory-functions.md#make_unique).

## <a name="see-also"></a>Viz také:

[Chytré ukazatele (moderní verze jazyka C++)](smart-pointers-modern-cpp.md)<br/>
[make_unique](../standard-library/memory-functions.md#make_unique)
