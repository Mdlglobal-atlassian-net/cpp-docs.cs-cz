---
title: 'Postupy: vytváření a používání instancí ukazatelů weak_ptr | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e51e523540e14905bef17edd52205c4d2102afa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-and-use-weakptr-instances"></a>Postupy: Vytváření a používání instancí ukazatelů weak_ptr
V některých případech musí objekt uložení přístup k základní objekt `shared_ptr` aniž by to způsobilo počet odkazů na se zvýší. Obvykle k této situaci dochází, když máte cyklické odkazy mezi `shared_ptr` instance.  
  
 Nejlepší návrhu se vyhnete sdílené vlastnictví ukazatele, kdykoli je to možné. Ale pokud musí mít sdílená vlastnictví `shared_ptr` instancí, vyhněte se cyklické odkazy mezi nimi. Pokud jsou cyklické odkazy nevyhnutelné použít, nebo i vhodnější z nějakého důvodu, použijte `weak_ptr` poskytnout jednu nebo více vlastníci slabé odkaz na jiný `shared_ptr`. Pomocí `weak_ptr`, můžete vytvořit `shared_ptr` , která se připojuje k existující sady souvisejících instancí, ale pouze pokud základní paměti prostředků je stále platné. A `weak_ptr` samotné neúčastní počítání odkazů, a proto ho nemůže zabránit počet odkazů přejdete na nulu. Můžete však použít `weak_ptr` pokusit se získat novou kopii `shared_ptr` s, který byl inicializován. Pokud byl již odstraněn paměť, **bad_weak_ptr** je vyvolána výjimka. Pokud velikost paměti je stále platné, nový sdílený ukazatel zvýší počet odkazů a zaručuje, že paměť bude platit, dokud `shared_ptr` zůstává proměnné v oboru.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje případu kde `weak_ptr` slouží k zajištění správné odstranění objektů, které mají cyklické závislosti. Jak byste zkontrolovat příklad, Předpokládejme, že byl vytvořili až poté, co se považuje za alternativní řešení. `Controller` Objekty představují některých aspektů procesu počítače a fungovat nezávisle. Každý řadič musí být schopný dotaz na stav se ostatní řadiče kdykoli a každé z nich obsahuje soukromé `vector<weak_ptr<Controller>>` pro tento účel. Každý vektoru obsahuje cyklický odkaz a proto `weak_ptr` instancí se používají místo `shared_ptr`.  
  
 [!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]  
  
```Output  
Creating Controller0Creating Controller1Creating Controller2Creating Controller3Creating Controller4push_back to v[0]: 1push_back to v[0]: 2push_back to v[0]: 3push_back to v[0]: 4push_back to v[1]: 0push_back to v[1]: 2push_back to v[1]: 3push_back to v[1]: 4push_back to v[2]: 0push_back to v[2]: 1push_back to v[2]: 3push_back to v[2]: 4push_back to v[3]: 0push_back to v[3]: 1push_back to v[3]: 2push_back to v[3]: 4push_back to v[4]: 0push_back to v[4]: 1push_back to v[4]: 2push_back to v[4]: 3use_count = 1Status of 1 = OnStatus of 2 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 2 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 2 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 2 = OnStatus of 3 = OnDestroying Controller0Destroying Controller1Destroying Controller2Destroying Controller3Destroying Controller4Press any key  
```  
  
 Jako experimentu, upravte vektoru `others` být `vector<shared_ptr<Controller>>`a potom ve výstupu, Všimněte si, že jsou spuštěny žádné destruktorů při `TestRun` vrátí.  
  
## <a name="see-also"></a>Viz také  
 [Chytré ukazatele](../cpp/smart-pointers-modern-cpp.md)