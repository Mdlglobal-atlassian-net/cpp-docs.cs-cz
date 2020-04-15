---
title: Rozhraní (C++/CX)
ms.date: 01/22/2017
ms.assetid: 11034314-d54a-426d-923b-5ab7a6b9f8ce
ms.openlocfilehash: b904f041e34bcf5fda78fed11aaad4998ba5208a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366043"
---
# <a name="interfaces-ccx"></a>Rozhraní (C++/CX)

Přestože ref třída může dědit maximálně z jedné konkrétní základní třídy, může implementovat libovolný počet tříd rozhraní. Třída rozhraní (nebo struktura rozhraní) sama o sobě může dědit (nebo vyžadovat) více tříd rozhraní, může přetížit své členské funkce a může mít parametry typu.

## <a name="characteristics"></a>Vlastnosti

Rozhraní má tyto vlastnosti:

- Třída rozhraní (nebo struktura) musí být deklarována v rámci oboru názvů a může mít veřejnou nebo soukromou přístupnost. Metadatům jsou vyzařována pouze veřejná rozhraní.

- Členové rozhraní mohou obsahovat vlastnosti, metody a události.

- Všechny členy rozhraní jsou implicitně veřejné a virtuální.

- Pole a statické členy nejsou povoleny.

- Typy, které se používají jako vlastnosti, parametry metody nebo vrácené hodnoty mohou být pouze typy prostředí Windows Runtime; to zahrnuje základní typy a typy tříd výčtu.

## <a name="declaration-and-usage"></a>Prohlášení a použití

Následující příklad ukazuje, jak deklarovat rozhraní. Všimněte si, že rozhraní lze deklarovat jako typ třídy nebo struktury.

[!code-cpp[cx_interfaces#01](../cppcx/codesnippet/CPP/interfacestest/class1.h#01)]

Chcete-li implementovat rozhraní, ref třídy nebo ref struct deklaruje a implementuje virtuální metody a vlastnosti. Rozhraní a implementující ref třídy musí používat stejné názvy parametrů metody, jak je znázorněno v tomto příkladu:

[!code-cpp[cx_interfaces#02](../cppcx/codesnippet/CPP/interfacestest/class1.h#02)]

## <a name="interface-inheritance-hierarchies"></a>Hierarchie dědičnosti rozhraní

Rozhraní může dědit z jednoho nebo více rozhraní. Ale na rozdíl od třídy ref nebo struktury rozhraní nedeklaruje zděděné členy rozhraní. Pokud rozhraní B dědí z rozhraní A a ref třídy C dědí z B, C musí implementovat a to i A a B. To je znázorněno v následujícím příkladu.

[!code-cpp[cx_interfaces#03](../cppcx/codesnippet/CPP/interfacestest/class1.h#03)]

## <a name="implementing-interface-properties-and-events"></a>Implementace vlastností a událostí rozhraní

Jak je znázorněno v předchozím příkladu, můžete použít triviální virtuální vlastnosti k implementaci vlastností rozhraní. Můžete také poskytnout vlastní getters a setters v implementující třídě.  Getter a setter musí být veřejné ve vlastnosti rozhraní.

[!code-cpp[cx_interfaces#04](../cppcx/codesnippet/CPP/interfacestest/class1.h#04)]

Pokud rozhraní deklaruje get-only nebo set pouze vlastnost, pak implementující třída by měla explicitně poskytnout getter nebo setter.

[!code-cpp[cx_interfaces#05](../cppcx/codesnippet/CPP/interfacestest/class1.h#05)]

Můžete také implementovat vlastní přidat a odebrat metody pro události v implementující třídě.

## <a name="explicit-interface-implementation"></a>Explicitní implementace rozhraní

Když třída ref implementuje více rozhraní a tato rozhraní mají metody, jejichž názvy a podpisy jsou shodné s kompilátorem, můžete použít následující syntaxi explicitně označit metodu rozhraní, kterou implementuje metoda třídy.

[!code-cpp[cx_interfaces#06](../cppcx/codesnippet/CPP/interfacestest/class1.h#06)]

## <a name="generic-interfaces"></a>Obecná rozhraní

V jazyce C++/CX se `generic` klíčové slovo používá k reprezentaci parametrizovaného typu prostředí Windows Runtime. Parametrizovaný typ je emitován v metadatech a může být spotřebován kódem, který je napsán v libovolném jazyce, který podporuje parametry typu. Prostředí Windows Runtime definuje některá obecná rozhraní – například [Windows::Foundation::Collections::IVector\<T>](/uwp/api/Windows.Foundation.Collections.IVector_T_)– ale nepodporuje vytváření veřejných uživatelem definovaných obecných rozhraní v jazyce C++/CX. Můžete však vytvořit privátní obecná rozhraní.

Zde je návod, jak windows runtime typy lze použít k vytvoření obecné rozhraní:

- Obecný uživatel definovaný `interface class` v komponentě nesmí být emitován do souboru metadat systému Windows. proto nemůže mít veřejnou přístupnost a klientský kód v jiných souborech .winmd jej nemůže implementovat. Může být implementována neveřejnými třídami ref ve stejné součásti. Třída veřejného ref může mít obecný typ rozhraní jako soukromý člen.

   Následující fragment kódu ukazuje, jak deklarovat obecný `interface class` a pak jej implementovat v soukromé ref třídy a použít ref třídy jako soukromý člen ve veřejné ref třídy.

   [!code-cpp[cx_interfaces#07](../cppcx/codesnippet/CPP/interfacestest/class1.h#07)]

- Obecné rozhraní musí dodržovat standardní pravidla rozhraní, která řídí usnadnění přístupu, členy, *vyžaduje* vztahy, základní třídy a tak dále.

- Obecné rozhraní může trvat jeden nebo více obecných `typename` `class`parametrů typu, které předchází nebo . Parametry bez typu nejsou podporovány.

- Parametr typu může být libovolný typ prostředí Windows Runtime. To znamená, že parametr typu může být typ odkazu, typ hodnoty, třída rozhraní, delegát, základní typ nebo třída veřejnévýčtovky výčtu.

- *Uzavřené obecné rozhraní* je rozhraní, které dědí z obecného rozhraní a určuje konkrétní argumenty typu pro všechny parametry typu. Lze použít kdekoli, že lze použít neobecné privátní rozhraní.

- *Otevřené obecné rozhraní* je rozhraní, které má jeden nebo více parametrů typu, pro které ještě není k dispozici žádný konkrétní typ. Lze použít kdekoli, že typ lze použít, včetně jako argument typu jiného obecného rozhraní.

- Parametrizovat lze pouze celé rozhraní, nikoli jednotlivé metody.

- Parametry typu nelze omezit.

- Uzavřené obecné rozhraní má implicitně generované UUID. Uživatel nemůže zadat UUID.

- V rozhraní se předpokládá, že jakýkoli odkaz na aktuální rozhraní – v parametru metody, vrácené hodnotě nebo vlastnosti – odkazuje na aktuální instanci. Například *IMyIntf* znamená *IMyIntf\<T>*.

- Pokud je typem parametru metody parametr typu, deklarace tohoto parametru nebo proměnné použije název parametru typu bez jakéhokoli ukazatele, nativního odkazu nebo deklarátorů zpracování. Jinými slovy, nikdy nepíšete "T^".

- Šablony ref třídy musí být soukromé. Mohou implementovat obecná rozhraní a mohou předat parametr šablony *T* obecnému argumentu *T*. Každá instance šablony ref třídy je sama o sobě ref třídy.

## <a name="see-also"></a>Viz také

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
