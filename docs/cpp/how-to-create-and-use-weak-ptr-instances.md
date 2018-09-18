---
title: 'Postupy: vytváření a používání instancí ukazatelů weak_ptr | Dokumentace Microsoftu'
ms.custom: how-to
ms.date: 07/12/2018
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fe982762c6e6c44b8f1923d27779bcfd6140225
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087698"
---
# <a name="how-to-create-and-use-weakptr-instances"></a>Postupy: Vytváření a používání instancí ukazatelů weak_ptr

Někdy musí objekt uložit cestu pro přístup k objektu `shared_ptr` aniž by došlo k navýšení počtu odkazů. Obvykle k této situaci dochází, když máte cyklické odkazy mezi `shared_ptr` instancí.

Nejlepší je vyhnout se sdílenému vlastnictví ukazatelů, kdykoli je to možné. Nicméně pokud musíte mít sdílené vlastnictví `shared_ptr` instancí, vyhněte se cyklickým odkazům mezi nimi. Pokud z nějakého důvodu jsou cyklické odkazy nevyhnutelné nebo dokonce výhodnější, použijte `weak_ptr` poskytnout jednu nebo více vlastníkům nestálý odkaz na jiný `shared_ptr`. Pomocí `weak_ptr`, můžete vytvořit `shared_ptr` , který se připojí k existující sadě souvisejících instancí, ale pouze pokud jsou prostředky základní paměti stále platné. A `weak_ptr` sám se neúčastní počítání odkazů, a proto ji nelze zabránit počet odkazů v dosažení nuly. Můžete však použít `weak_ptr` pro pokus o získání nové kopie `shared_ptr` s kterou byla inicializována. Je-li paměť již byla odstraněna, `bad_weak_ptr` je vyvolána výjimka. Pokud je paměť stále platná, nový sdílený ukazatel zvýší počet odkazů a zaručuje, že paměť bude platit za předpokladu, `shared_ptr` proměnná zůstane v oboru.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje případ kde `weak_ptr` se používá k zajištění řádného odstranění objektů, které mají cyklické závislosti. Při prohlížení příkladu, se předpokládá, že byl vytvořen pouze poté, co byla zvážena alternativní řešení. `Controller` Objekty představují některé aspekty procesu počítače a fungují nezávisle na sobě. Každý řadič musí být schopen kdykoli zjistit stav ostatních řadičů a každý z nich obsahuje privátní `vector<weak_ptr<Controller>>` pro tento účel. Každý vektor obsahuje cyklický odkaz a proto `weak_ptr` instancí se používají místo `shared_ptr`.

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
Status of 0 = O
nStatus of 1 = On
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

Jako experiment upravte vektor `others` bude `vector<shared_ptr<Controller>>`a potom ve výstupu Všimněte si, že nejsou vyvolány žádné destruktory při `TestRun` vrátí.

## <a name="see-also"></a>Viz také:

[Inteligentní ukazatele](../cpp/smart-pointers-modern-cpp.md)