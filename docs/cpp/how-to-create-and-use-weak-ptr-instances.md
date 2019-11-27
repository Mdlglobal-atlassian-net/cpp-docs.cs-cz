---
title: 'Postupy: vytváření a používání instancí weak_ptr'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: 32e8d64fdb6449f1d40aec4161bfda54987ca66a
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245605"
---
# <a name="how-to-create-and-use-weak_ptr-instances"></a>Postupy: vytváření a používání instancí weak_ptr

V některých případech musí objekt ukládat způsob, jak přistupovat k základnímu objektu [shared_ptr](../standard-library/shared-ptr-class.md) , aniž by došlo k zvýšení počtu odkazů. K této situaci obvykle dochází, když máte cyklické odkazy mezi instancemi `shared_ptr`.

Nejlepším návrhem je vyhnout se sdílenému vlastnictví ukazatelů, kdykoli můžete. Pokud však potřebujete sdílené vlastnictví instancí `shared_ptr`, vyhněte se cyklickým odkazům mezi nimi. Pokud jsou cyklické odkazy nenevyhnutelné nebo dokonce vhodnější z nějakého důvodu, použijte [weak_ptr](../standard-library/weak-ptr-class.md) k tomu, aby jeden nebo více vlastníků poskytovaly slabý odkaz na jiný `shared_ptr`. Pomocí `weak_ptr`můžete vytvořit `shared_ptr`, která se připojí k existující sadě souvisejících instancí, ale pouze v případě, že je základní paměťový prostředek stále platný. `weak_ptr` sám se neúčastní počítání odkazů, a proto nemůže zabránit počtu odkazů v přechodu na nulu. Můžete však použít `weak_ptr` k pokusu o získání nové kopie `shared_ptr`, se kterou byla inicializována. Pokud je paměť již odstraněna, vrátí operátor bool `weak_ptr``false`. Pokud je paměť stále platná, nový sdílený ukazatel zvýší počet odkazů a zaručí, že paměť bude platná, dokud `shared_ptr` proměnná zůstane v rozsahu.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje případ, kdy `weak_ptr` slouží k zajištění správného odstranění objektů, které mají cyklické závislosti. Při kontrole příkladu Předpokládejme, že byl vytvořen až po zvážení alternativních řešení. Objekty `Controller` představují určitý aspekt procesu počítače a pracují nezávisle. Každý kontroler musí být schopný dotazovat se na stav jiných řadičů kdykoli a každý z nich obsahuje privátní `vector<weak_ptr<Controller>>` pro tento účel. Každý vektor obsahuje cyklický odkaz, a proto se místo `shared_ptr`používá instance `weak_ptr`.

[!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]

```Output
Creating Controller0
Creating Controller1
Creating Controller2
Creating Controller3
Creating Controller4
push_back to v[0]: 1
push_back to v[0]: 2
push_back to v[0]: 3
push_back to v[0]: 4
push_back to v[1]: 0
push_back to v[1]: 2
push_back to v[1]: 3
push_back to v[1]: 4
push_back to v[2]: 0
push_back to v[2]: 1
push_back to v[2]: 3
push_back to v[2]: 4
push_back to v[3]: 0
push_back to v[3]: 1
push_back to v[3]: 2
push_back to v[3]: 4
push_back to v[4]: 0
push_back to v[4]: 1
push_back to v[4]: 2
push_back to v[4]: 3
use_count = 1
Status of 1 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 2 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 2 = On
Status of 3 = On
Destroying Controller0
Destroying Controller1
Destroying Controller2
Destroying Controller3
Destroying Controller4
Press any key
```

Jako experiment upravte `others` vektoru jako `vector<shared_ptr<Controller>>`a potom ve výstupu Všimněte si, že při `TestRun` vrácení vrátí žádné destruktory.

## <a name="see-also"></a>Viz také:

[Chytré ukazatele (moderní verze jazyka C++)](../cpp/smart-pointers-modern-cpp.md)
