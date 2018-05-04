---
title: 'Postupy: vytváření a používání instancí ukazatelů unique_ptr | Microsoft Docs'
ms.custom: how-to
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82cf4fb475f9c89a4a088cac9d5ee0e1231d436e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-create-and-use-uniqueptr-instances"></a>Postupy: Vytváření a používání instancí ukazatelů unique_ptr
A [unique_ptr](../standard-library/unique-ptr-class.md) nesdílí jeho ukazatele. Nemůže být zkopírován do jiného `unique_ptr`, podle hodnoty předaný funkci nebo použít v jakékoli standardní knihovna C++ algoritmus, který vyžaduje kopie má být provedeno. A `unique_ptr` se dá přesunout jedině. To znamená, že vlastnictví prostředků paměti je přenášet do jiného `unique_ptr` a původní `unique_ptr` už je jeho vlastníkem. Doporučujeme omezit objekt na jednoho vlastníka, protože více vlastnictví zkomplikuje programovou logiku. Proto když potřebujete chytré ukazatele pro objekt prostý C++, použít `unique_ptr`, a když vytvoříte `unique_ptr`, použijte [make_unique](../standard-library/memory-functions.md#make_unique) pomocné funkce.  
  
 Následující diagram znázorňuje přenos vlastnictví mezi dvěma `unique_ptr` instance.  
  
 ![Přesunutí vlastnictví jedinečný&#95;ptr](../cpp/media/unique_ptr.png "unique_ptr")  
  
 `unique_ptr` je definována v `<memory>` záhlaví ve standardní knihovně C++. Je přesně je efektivní jako nezpracovaná ukazatel a lze použít v kontejnerech standardní knihovna C++. Přidání `unique_ptr` instancí standardní knihovna C++ kontejnery je efektivní protože konstruktoru přesunout `unique_ptr` eliminuje potřebu operace kopírování.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `unique_ptr` instancí a jejich předání funkce.  
  
 [!code-cpp[stl_smart_pointers#210](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]  
  
 Tyto příklady ukazují tuto základní vlastnosti `unique_ptr`: můžete být přesunuta, ale není zkopírovali. "Přesun" přenos vlastnictví na nový `unique_ptr` a resetuje starý `unique_ptr`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `unique_ptr` instance a použijte je v vektor.  
  
 [!code-cpp[stl_smart_pointers#211](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]  
  
 V rozsahu pro smyčky, Všimněte si, že `unique_ptr` je předána odkazem. Pokud se pokusíte předat zde hodnotou, bude kompilátor vyvolá chybu, protože `unique_ptr` kopírovací konstruktor se odstraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k chybě při inicializaci `unique_ptr` tedy člena třídy.  
  
 [!code-cpp[stl_smart_pointers#212](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]  
  
## <a name="example"></a>Příklad  
 Můžete použít [make_unique](../standard-library/memory-functions.md#make_unique) k vytvoření `unique_ptr` do pole, ale nemůžete použít `make_unique` k chybě při inicializaci prvků pole.  
  
 [!code-cpp[stl_smart_pointers#213](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]  
  
 Další příklady najdete v tématu [make_unique](../standard-library/memory-functions.md#make_unique).  
  
## <a name="see-also"></a>Viz také  
 [Chytré ukazatele](../cpp/smart-pointers-modern-cpp.md)   
 [make_unique](../standard-library/memory-functions.md#make_unique)