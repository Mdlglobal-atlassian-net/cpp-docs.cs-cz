---
title: 'Postupy: Vytváření a používání instancí ukazatelů unique_ptr'
ms.custom: how-to
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
ms.openlocfilehash: a3e5705b47a4cfdf17b9a4b4829f1e13565dd7ce
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52174869"
---
# <a name="how-to-create-and-use-uniqueptr-instances"></a>Postupy: Vytváření a používání instancí ukazatelů unique_ptr

A [unique_ptr](../standard-library/unique-ptr-class.md) nesdílí jeho ukazatel. Nemůže být zkopírován do jiného `unique_ptr`, předán podle hodnoty do funkce, nebo použit v libovolném algoritmu standardní knihovny C++, který vyžaduje vytvoření kopií, které budou. A `unique_ptr` lze pouze přesunout. To znamená, že vlastnictví prostředku paměti je převedeno do jiného `unique_ptr` a původní `unique_ptr` není nadále jeho vlastníkem. Doporučujeme omezit objekt na jednoho vlastníka, protože více vlastnictví zkomplikuje programovou logiku. Proto, když budete potřebovat inteligentní ukazatel pro prostý objekt jazyka C++, použijte `unique_ptr`, a při sestavování `unique_ptr`, použijte [make_unique](../standard-library/memory-functions.md#make_unique) pomocnou funkci.

Následující diagram znázorňuje převod vlastnictví mezi dvěma `unique_ptr` instancí.

![Přesunutí vlastnictví jedinečný&#95;ptr](../cpp/media/unique_ptr.png "přesun vlastnictví jedinečný&#95;ptr")

`unique_ptr` je definován v `<memory>` záhlaví ve standardní knihovně jazyka C++. To je přesně tak efektivní jako nezpracovaný ukazatel a lze použít v kontejnery standardní knihovny C++. Přidání `unique_ptr` instance pro kontejnery standardní knihovny C++ je efektivnější protože konstruktor přesunu `unique_ptr` eliminuje potřebu operace kopírování.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `unique_ptr` instance a předat je mezi funkcemi.

[!code-cpp[stl_smart_pointers#210](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]

Tyto příklady ukazují tuto základní charakteristiku `unique_ptr`: lze je přesunout, ale ne zkopírovat. "Přesun" převede vlastnictví na novou `unique_ptr` a obnoví původní `unique_ptr`.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `unique_ptr` instance a používat je ve vektoru.

[!code-cpp[stl_smart_pointers#211](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]

V rozsahu smyčky si všimněte, `unique_ptr` je předána odkazem. Pokud se pokusíte předat hodnotu v tomto poli, vyvolá kompilátor chybu vzhledem k tomu, `unique_ptr` konstruktor kopie je odstraněna.

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob inicializace `unique_ptr` , který je členem třídy.

[!code-cpp[stl_smart_pointers#212](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]

## <a name="example"></a>Příklad

Můžete použít [make_unique](../standard-library/memory-functions.md#make_unique) k vytvoření `unique_ptr` na pole, ale nemůžete použít `make_unique` k inicializaci prvků pole.

[!code-cpp[stl_smart_pointers#213](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]

Další příklady najdete v tématu [make_unique](../standard-library/memory-functions.md#make_unique).

## <a name="see-also"></a>Viz také:

[Inteligentní ukazatele](../cpp/smart-pointers-modern-cpp.md)<br/>
[make_unique](../standard-library/memory-functions.md#make_unique)