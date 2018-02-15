---
title: "Rozhraní (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 11034314-d54a-426d-923b-5ab7a6b9f8ce
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aa87713b49fe41dbdb7eb8f9e6382c8f78b51d0c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="interfaces-ccx"></a>Rozhraní (C + +/ CX)
I když třídu ref může dědit vlastnosti z maximálně jednu konkrétní základní třídu, můžete implementovat libovolný počet třídy rozhraní. Třída rozhraní (nebo struktura rozhraní) sám sebe může dědit (nebo vyžadovat) více rozhraní třídy, může přetížit jeho členských funkcí a může mít parametry typu.  
  
## <a name="characteristics"></a>Vlastnosti  
 Rozhraní má tyto vlastnosti:  
  
-   Třída rozhraní (nebo struktura) musí být deklarován v oboru názvů a může mít veřejných nebo privátních usnadnění. Na metadata jsou vydávány pouze veřejné rozhraní.  
  
-   Členové rozhraní může obsahovat vlastnosti, metod a události.  
  
-   Všechny členy rozhraní jsou implicitně veřejné a virtuální.  
  
-   Pole a statické členy nejsou povoleny.  
  
-   Typy, které jsou použity jako parametry metody, vlastnosti nebo návratové hodnoty lze pouze typy prostředí Windows Runtime; To zahrnuje základní typy a typy výčtu tříd.  
  
## <a name="declaration-and-usage"></a>Deklarace a používání  
 Následující příklad ukazuje, jak rozhraní deklarovat. Všimněte si, že rozhraní může být deklarován jako typ třídě nebo struktuře.  
  
 [!code-cpp[cx_interfaces#01](../cppcx/codesnippet/CPP/interfacestest/class1.h#01)]  
  
 Pokud chcete implementovat rozhraní, ref třídě nebo struktuře ref deklaruje a implementuje virtuální metody a vlastnosti. Rozhraní a implementující třídu ref musí používat stejné názvy parametrů metoda, jak je uvedeno v následujícím příkladu:  
  
 [!code-cpp[cx_interfaces#02](../cppcx/codesnippet/CPP/interfacestest/class1.h#02)]  
  
## <a name="interface-inheritance-hierarchies"></a>Hierarchie dědičnosti rozhraní  
 Rozhraní může dědit vlastnosti z jednoho nebo více rozhraní. Ale na rozdíl od ref třídě nebo struktuře, nepodporuje rozhraní deklarovat rozhraní zděděné členy. Pokud rozhraní B zdědí rozhraní A a ref třída C dědí z B, C musí implementovat, jak a B. To je znázorněno v následujícím příkladu.  
  
 [!code-cpp[cx_interfaces#03](../cppcx/codesnippet/CPP/interfacestest/class1.h#03)]  
  
## <a name="implementing-interface-properties-and-events"></a>Implementace rozhraní vlastností a událostí  
 Jak ukazuje předchozí příklad, můžete implementovat rozhraní vlastnosti trivial virtuální vlastnosti. Můžete také zadat vlastní mechanismy získání a nastavení v implementující třídu.  Metoda getter a setter metody musí být veřejné ve vlastnosti rozhraní.  
  
 [!code-cpp[cx_interfaces#04](../cppcx/codesnippet/CPP/interfacestest/class1.h#04)]  
  
 Pokud rozhraní deklaruje jen get, nebo jenom sadu vlastností, implementující třídu musí explicitně zadejte getter a setter.  
  
 [!code-cpp[cx_interfaces#05](../cppcx/codesnippet/CPP/interfacestest/class1.h#05)]  
  
 Můžete implementovat vlastní přidávat a odebírat metody pro události v implementující třídu.  
  
## <a name="explicit-interface-implementation"></a>Implementace explicitního rozhraní  
 Když ref třída implementuje více rozhraní a těchto rozhraní mají metody, jejichž názvy a podpisy jsou identické pro kompilátor, můžete tuto syntaxi explicitně označíte, metody rozhraní, která implementuje metody třídy.  
  
 [!code-cpp[cx_interfaces#06](../cppcx/codesnippet/CPP/interfacestest/class1.h#06)]  
  
## <a name="generic-interfaces"></a>Obecná rozhraní  
 V jazyce C + +/ CX, `generic` – klíčové slovo se používá k reprezentování typu prostředí Windows Runtime s parametry. Parametrizované typ je vygenerované v metadatech a mohou být spotřebovávána kód, který je napsán v libovolném jazyce, který podporuje parametry typu. Prostředí Windows Runtime definuje některé obecná rozhraní – například [Windows::Foundation::Collections::IVector\<T >](Windows::Foundation::Collections::IVector)– ale nepodporuje vytvoření veřejné uživatelem definované obecná rozhraní v jazyce C + +/ CX. Ale můžete vytvořit privátní obecná rozhraní.  
  
 Tady je použití prostředí Windows Runtime typy vytvářet generické rozhraní:  
  
-   Obecný uživatelem definované `interface class` v součást není povoleno do jeho soubor metadat Windows; proto nemůže mít veřejnou dostupnost a kód klienta v jiné soubory .winmd nelze implementaci. Může být implementována neveřejný ref tříd ve stejné komponenty. Třída veřejné ref může mít obecné rozhraní, zadejte jako soukromý člen.  
  
     Následující fragment kódu ukazuje, jak deklarovat obecný `interface class` a implementovat v privátní ref třídu a použijte třídu ref jako soukromý člen v třídě veřejné ref.  
  
     [!code-cpp[cx_interfaces#07](../cppcx/codesnippet/CPP/interfacestest/class1.h#07)]  
  
-   Generické rozhraní třeba postupovat podle standardního rozhraní pravidla, která řídí usnadnění, členy, *vyžaduje* relace, základní třídy a tak dále.  
  
-   Generické rozhraní může trvat jeden nebo více parametrů obecného typu, které předchází `typename` nebo `class`. Parametry bez typu nejsou podporovány.  
  
-   Parametr typu mohou být jakéhokoli typu prostředí Windows Runtime. To znamená parametr typu může být odkazového typu, typ hodnoty, třídu rozhraní, delegáta, základní typ nebo veřejný výčet tříd.  
  
-   A *uzavřený obecné rozhraní* je rozhraní, která dědí z obecné rozhraní a určuje konkrétní typ argumenty pro všechny parametry typu. Ho lze použít kdekoli lze neobecnou soukromé rozhraní.  
  
-   *Otevřete obecné rozhraní* je rozhraní, které obsahuje jeden nebo více parametrů typu, pro které se ještě poskytuje žádný konkrétní typ. Ho lze použít kdekoli, typu lze použít jako argument typu jiné obecné rozhraní včetně.  
  
-   Můžete parametrizovat pouze celý rozhraní, ne u jednotlivých metod.  
  
-   Parametry typu nemůže být omezen.  
  
-   Uzavřené obecné rozhraní má implicitně generovaného UUID. Uživatele nelze zadat identifikátor UUID.  
  
-   V rozhraní, žádný odkaz na aktuální rozhraní – v parametru metody, vrátí hodnotu, nebo vlastnost – se předpokládá, že k odkazování na aktuální instance. Například *IMyIntf* znamená *IMyIntf\<T >*.  
  
-   Pokud parametr typu je typ parametru metody, deklaraci tento parametr nebo proměnná používá název parametr typu bez jakýchkoli ukazatele, nativní referenční dokumentace nebo deklarátory popisovač. Jinými slovy, nikdy zápisu "T ^".  
  
-   Třídy šablonované ref musí být privátní. Můžete implementovat obecné rozhraní a můžete předat parametr šablony *T* na obecné argument *T*. Každý vytváření instancí třídy šablonované ref samotné je třída ref.  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)