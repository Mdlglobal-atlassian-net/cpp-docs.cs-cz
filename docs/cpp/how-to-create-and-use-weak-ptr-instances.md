---
title: 'Postupy: Vytváření a používání instancí weak_ptr'
ms.custom: how-to
ms.date: 09/18/2019
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: e5d1b13d894a617ca514e26f14fde3f514540d34
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127182"
---
# <a name="how-to-create-and-use-weak_ptr-instances"></a>Postupy: Vytváření a používání instancí weak_ptr

V některých případech musí objekt ukládat způsob, jak přistupovat k základnímu objektu `shared_ptr` a bez toho, aby bylo možné zvýšit počet odkazů. K této situaci obvykle dochází, když máte cyklické odkazy mezi `shared_ptr` instancemi.

Nejlepším návrhem je vyhnout se sdílenému vlastnictví ukazatelů, kdykoli můžete. Pokud však musíte mít sdílené vlastnictví `shared_ptr` instancí, vyhněte se cyklickým odkazům mezi nimi. Pokud jsou cyklické odkazy nenevyhnutelné nebo dokonce vhodnější z nějakého důvodu, použijte `weak_ptr` k tomu, aby jeden nebo více vlastníků poskytoval slabý odkaz na jiný. `shared_ptr` Pomocí nástroje `weak_ptr`můžete `shared_ptr` vytvořit spojení s existující sadou souvisejících instancí, ale pouze pokud je základní paměťový prostředek stále platný. Sám `weak_ptr` o sobě se neúčastní počítání odkazů, a proto nemůže zabránit tomu, aby se počet odkazů přečetl na nulu. Můžete však použít `weak_ptr` k pokusu o získání nové kopie, `shared_ptr` pomocí které byla inicializována. Pokud je paměť již odstraněna, vrátí `weak_ptr` `false`se operátor bool. Pokud je paměť stále platná, nový sdílený ukazatel zvýší počet odkazů a zaručí, že paměť bude platná, dokud `shared_ptr` proměnná zůstane v oboru.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje případ, kde `weak_ptr` se používá k zajištění správného odstranění objektů, které mají cyklické závislosti. Při kontrole příkladu Předpokládejme, že byl vytvořen až po zvážení alternativních řešení. `Controller` Objekty představují nějaký aspekt procesu počítače a pracují nezávisle. Každý kontroler musí být schopný dotazovat se na stav jiných řadičů kdykoli a každý z nich obsahuje pro tento účel privátní `vector<weak_ptr<Controller>>` . Každý vektor obsahuje cyklický odkaz, a proto `weak_ptr` se `shared_ptr`místo toho používají instance.

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

V rámci experimentu změňte vektor `others` tak `vector<shared_ptr<Controller>>`, aby byl a pak ve výstupu Všimněte si, že při `TestRun` návratu nejsou vyvolány žádné destruktory.

## <a name="see-also"></a>Viz také:

[Chytré ukazatele (moderní verze jazyka C++)](../cpp/smart-pointers-modern-cpp.md)
