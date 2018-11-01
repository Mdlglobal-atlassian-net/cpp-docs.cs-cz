---
title: Rozhraní (C + +/ CX)
ms.date: 01/22/2017
ms.assetid: 11034314-d54a-426d-923b-5ab7a6b9f8ce
ms.openlocfilehash: 33fe0df457a4f1bab3a7cffab585501364d5750c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626626"
---
# <a name="interfaces-ccx"></a>Rozhraní (C + +/ CX)

I když třídy ref class. může dědit z maximálně jeden konkrétní základní třídy, může implementovat libovolný počet tříd rozhraní. Třída rozhraní (nebo interface struct) samotné mohou dědit (nebo vyžadují) více rozhraní třídy, mohou přetížit její členské funkce a může mít parametry typu.

## <a name="characteristics"></a>Vlastnosti

Rozhraní má tyto vlastnosti:

- Třída rozhraní (nebo struct) musí být deklarovány v oboru názvů a může mít přístup k veřejné nebo soukromé. Jenom veřejné rozhraní jsou emitovány do metadat.

- Členy rozhraní může obsahovat vlastnosti, metody a události.

- Všechny členy rozhraní jsou implicitně veřejné i virtuální.

- Pole a statické členy nejsou povolené.

- Typy, které se používají jako vlastnosti, metody parametry nebo návratové hodnoty mohou být pouze typy modulu Windows Runtime; To zahrnuje základní typy a typy tříd výčtu.

## <a name="declaration-and-usage"></a>Deklarace a používání

Následující příklad ukazuje, jak deklarovat rozhraní. Všimněte si, že rozhraní mohou být deklarovány jako typ třídy nebo struktury.

[!code-cpp[cx_interfaces#01](../cppcx/codesnippet/CPP/interfacestest/class1.h#01)]

Implementovat rozhraní, třídy ref class nebo ref struct deklaruje a implementuje virtuální metody a vlastnosti. Rozhraní a implementující třída ref musí používat stejné názvy parametrů metody, jak je znázorněno v tomto příkladu:

[!code-cpp[cx_interfaces#02](../cppcx/codesnippet/CPP/interfacestest/class1.h#02)]

## <a name="interface-inheritance-hierarchies"></a>Hierarchie dědičnosti rozhraní

Rozhraní může dědit z jednoho nebo více rozhraní. Ale na rozdíl od třídy ref class nebo struct rozhraní nelze deklarovat členy zděděné rozhraní. Pokud rozhraní B dědí z rozhraní A a referenční třídy jazyka C je odvozen z B, C musí implementovat i B. To je ukázáno v následujícím příkladu.

[!code-cpp[cx_interfaces#03](../cppcx/codesnippet/CPP/interfacestest/class1.h#03)]

## <a name="implementing-interface-properties-and-events"></a>Implementace rozhraní vlastnosti a události.

Jak je znázorněno v předchozím příkladu, můžete k implementaci rozhraní vlastnosti triviální vlastnosti virtuální. Můžete taky zadat vlastní gettery a settery v implementující třídu.  Metoda getter a setter musí být veřejné ve vlastnosti rozhraní.

[!code-cpp[cx_interfaces#04](../cppcx/codesnippet/CPP/interfacestest/class1.h#04)]

Pokud rozhraní deklaruje jenom pro získání nebo jenom sadu vlastností, implementující třída by měla explicitně zadejte getter nebo setter.

[!code-cpp[cx_interfaces#05](../cppcx/codesnippet/CPP/interfacestest/class1.h#05)]

Můžete také implementovat vlastní přidání a odebrání metody pro události v implementující třídu.

## <a name="explicit-interface-implementation"></a>Implementace explicitního rozhraní

Když třídy ref class implementuje více rozhraní a tato rozhraní mají metody, jejichž názvy a podpisy jsou stejné jako kompilátor, můžete explicitně určit metodu rozhraní, která implementuje metodu třídy následující syntaxi.

[!code-cpp[cx_interfaces#06](../cppcx/codesnippet/CPP/interfacestest/class1.h#06)]

## <a name="generic-interfaces"></a>Obecná rozhraní

V jazyce C + +/ CX, `generic` – klíčové slovo se používá k reprezentování typ Windows Runtime s parametry. Typ s parametry je vygenerován v metadatech a mohou být spotřebovány kód, který je napsané v libovolném jazyce, který podporuje parametry typu. Modul Windows Runtime definuje některé obecná rozhraní – například [Windows::Foundation::Collections::IVector\<T >](Windows::Foundation::Collections::IVector)– ale nepodporuje vytvoření veřejné uživatelem definované obecných rozhraní v jazyce C + +/ CX. Však můžete vytvořit privátní obecná rozhraní.

Tady je použití typů Windows Runtime autorovi generické rozhraní:

- Obecný uživatelský `interface class` v součásti nesmí být vložen do jeho soubor metadat Windows; proto nemůže mít přístupnost public a klientský kód v jiných souborech .winmd jeho implementaci. Může být implementována neveřejné referenční třídy pod stejnou komponentou. Třída public ref class může mít obecné rozhraní, zadejte jako privátní člen.

   Následující fragment kódu ukazuje, jak deklarovat obecný `interface class` a implementovat v privátní ref class a použití třídy ref jako privátní člen třída public ref class.

   [!code-cpp[cx_interfaces#07](../cppcx/codesnippet/CPP/interfacestest/class1.h#07)]

- Obecná rozhraní musí dodržovat standardní rozhraní pravidla, kterými se řídí přístupnost členů, *vyžaduje* relace, základní třídy a tak dále.

- Obecná rozhraní můžete provést jeden nebo více parametrů obecného typu, které předchází `typename` nebo `class`. Parametry bez typu nejsou podporovány.

- Typ parametru může být libovolný typ Windows Runtime. To znamená parametr typu může být typ odkazu, typ hodnoty, třída rozhraní, delegáta, základní typ nebo veřejný výčet tříd.

- A *uzavřený obecný rozhraní* je rozhraní, které dědí z obecné rozhraní a Určuje argumenty typu implementujícího typ pro všechny parametry typu. To lze použít kdekoli je možné privátní rozhraním neobecná.

- *Otevřít obecné rozhraní* je rozhraní, která má jeden nebo více parametrů typu, pro které žádný konkrétní typ neposkytujeme ještě. To lze použít kdekoli, že typ je možné, včetně jako argument typu jiného obecného rozhraní.

- Můžete parametrizovat pouze celé rozhraní, nikoli jednotlivé metody.

- Parametry typu nemůže být omezený.

- Uzavřený obecný rozhraní má implicitně generovaný identifikátor UUID. Uživatele nejde zadat identifikátor UUID.

- V rozhraní, všechny odkazy na aktuální rozhraní – v parametru metody, vrátí hodnotu, nebo vlastnost – se předpokládá, že odkazují na aktuální instanci. Například *IMyIntf* znamená, že *IMyIntf\<T >*.

- Pokud je typ parametru metody parametru typu, deklarace tento parametr nebo proměnná používá název parametru typu bez ukazatele, nativní odkaz nebo popisovač deklarátory. Jinými slovy, nikdy Nepsat "T ^".

- Bez vizuálního vzhledu referenční třídy musí být privátní. Můžete implementovat obecné rozhraní a můžete předat parametr šablony *T* obecný argument *T*. Každá instance třídy bez vizuálního vzhledu ref class samotného je třídy ref class.

## <a name="see-also"></a>Viz také

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)