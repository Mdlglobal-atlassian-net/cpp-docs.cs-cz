---
title: Rozhraní (C++/CX)
ms.date: 01/22/2017
ms.assetid: 11034314-d54a-426d-923b-5ab7a6b9f8ce
ms.openlocfilehash: 263feb7b9c8a472a6077236596107bdeff26a5a4
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740191"
---
# <a name="interfaces-ccx"></a>Rozhraní (C++/CX)

I když referenční třída může dědit z maximálně jedné konkrétní základní třídy, může implementovat libovolný počet tříd rozhraní. Třída rozhraní (nebo struktura rozhraní) sama může dědit (nebo vyžadovat) více tříd rozhraní, může přetížit své členské funkce a může mít parametry typu.

## <a name="characteristics"></a>Svých

Rozhraní má tyto vlastnosti:

- Třída rozhraní (nebo struktura) musí být deklarována v rámci oboru názvů a může mít veřejný nebo privátní přístupnost. Metadatům jsou generována pouze veřejná rozhraní.

- Členové rozhraní mohou zahrnovat vlastnosti, metody a události.

- Všechny členy rozhraní jsou implicitně veřejné a virtuální.

- Pole a statické členy nejsou povoleny.

- Typy, které jsou používány jako vlastnosti, parametry metody nebo návratové hodnoty, mohou být pouze prostředí Windows Runtime typy; To zahrnuje základní typy a typy třídy výčtu.

## <a name="declaration-and-usage"></a>Deklarace a použití

Následující příklad ukazuje, jak deklarovat rozhraní. Všimněte si, že rozhraní lze deklarovat jako typ třídy nebo struktury.

[!code-cpp[cx_interfaces#01](../cppcx/codesnippet/CPP/interfacestest/class1.h#01)]

Chcete-li implementovat rozhraní, třída ref class nebo ref struct deklaruje a implementuje virtuální metody a vlastnosti. Rozhraní a implementující referenční třída musí používat stejné názvy parametrů metody, jak je znázorněno v následujícím příkladu:

[!code-cpp[cx_interfaces#02](../cppcx/codesnippet/CPP/interfacestest/class1.h#02)]

## <a name="interface-inheritance-hierarchies"></a>Hierarchie dědičnosti rozhraní

Rozhraní může dědit z jednoho nebo více rozhraní. Ale na rozdíl od ref class nebo struct rozhraní nedeklaruje zděděné členy rozhraní. Pokud rozhraní B dědí z rozhraní a a ref class C dědí z B, C musí implementovat a a B. Toto je zobrazeno v následujícím příkladu.

[!code-cpp[cx_interfaces#03](../cppcx/codesnippet/CPP/interfacestest/class1.h#03)]

## <a name="implementing-interface-properties-and-events"></a>Implementace vlastností rozhraní a událostí

Jak je znázorněno v předchozím příkladu, můžete použít triviální virtuální vlastnosti k implementaci vlastností rozhraní. Můžete také poskytnout vlastní metody getter a setter v implementaci třídy.  Metoda getter i setter musí být veřejná ve vlastnosti rozhraní.

[!code-cpp[cx_interfaces#04](../cppcx/codesnippet/CPP/interfacestest/class1.h#04)]

Pokud rozhraní deklaruje vlastnost pouze pro získání nebo pouze pro nastavení, pak implementující třída musí explicitně poskytnout metodu getter nebo setter.

[!code-cpp[cx_interfaces#05](../cppcx/codesnippet/CPP/interfacestest/class1.h#05)]

Můžete také implementovat vlastní metody Add a Remove pro události v implementaci třídy.

## <a name="explicit-interface-implementation"></a>Explicitní implementace rozhraní

Když ref class implementuje více rozhraní a tato rozhraní mají metody, jejichž názvy a signatury jsou identické s kompilátorem, můžete pomocí následující syntaxe explicitně určit metodu rozhraní, kterou metoda třídy implementuje.

[!code-cpp[cx_interfaces#06](../cppcx/codesnippet/CPP/interfacestest/class1.h#06)]

## <a name="generic-interfaces"></a>Obecná rozhraní

V C++/CX, `generic` klíčové slovo slouží k reprezentaci prostředí Windows Runtime parametrizovaného typu. Parametrizovaný typ je generován v metadatech a lze jej spotřebovat kódem, který je napsán v jakémkoli jazyce, který podporuje parametry typu. Prostředí Windows Runtime definuje některá obecná rozhraní, například [Windows:: Foundation:: Collections:: IVector\<T >](Windows::Foundation::Collections::IVector), ale nepodporuje vytváření veřejných uživatelsky definovaných obecných rozhraní v C++/CX. Můžete však vytvořit privátní Obecná rozhraní.

Tady je postup, jak lze pomocí typů prostředí Windows Runtime vytvořit obecné rozhraní:

- Obecný uživatelsky definovaný `interface class` v komponentě není povoleno generovat do svého souboru metadat systému Windows. proto nemůže mít veřejnou přístupnost a klientský kód v jiných souborech. winmd nemůže implementovat. Může být implementováno neveřejnými referenčními třídami ve stejné komponentě. Veřejná referenční třída může mít jako soukromý člen typ obecného rozhraní.

   Následující fragment kódu ukazuje, jak deklarovat obecnou `interface class` a pak ji implementovat v soukromé referenční třídě a použít referenční třídu jako soukromý člen ve veřejné referenční třídě.

   [!code-cpp[cx_interfaces#07](../cppcx/codesnippet/CPP/interfacestest/class1.h#07)]

- Obecné rozhraní musí splňovat pravidla standardního rozhraní, která řídí přístupnost, členy, *vyžaduje* vztahy, základní třídy a tak dále.

- Obecné rozhraní může mít jeden nebo více parametrů obecného typu, které jsou uvozeny `typename` nebo. `class` Parametry bez typu nejsou podporovány.

- Parametr typu může být libovolný typ prostředí Windows Runtime. To znamená, že parametr typu může být odkazovým typem, typem hodnoty, třídou rozhraní, delegátem, základním typem nebo veřejnou třídou výčtu.

- *Uzavřené obecné rozhraní* je rozhraní, které dědí z obecného rozhraní a určuje konkrétní argumenty typu pro všechny parametry typu. Dá se použít kdekoli, kde se dá použít neobecné privátní rozhraní.

- *Otevřené obecné rozhraní* je rozhraní, které má jeden nebo více parametrů typu, pro které ještě nebyl poskytnut žádný konkrétní typ. Dá se použít kdekoli, kde lze použít typ, včetně jako argumentu typu jiného obecného rozhraní.

- Můžete parametrizovat pouze celé rozhraní, nikoli jednotlivé metody.

- Parametry typu nemůžou být omezené.

- Uzavřené obecné rozhraní má implicitně generovaný identifikátor UUID. Uživatel nemůže zadat UUID.

- V rozhraní se předpokládá, že všechny odkazy na aktuální rozhraní – v parametru metody, návratová hodnota nebo vlastnost – se předpokládá, že odkazují na aktuální instanciace. Například *IMyIntf* znamená *\<IMyIntf T >* .

- Když typ parametru metody je parametr typu, deklarace daného parametru nebo proměnné používá název parametru typu bez jakýchkoli ukazatelů, nativních odkazů nebo deklarátory popisovačů. Jinými slovy, nikdy nepíšete "T ^".

- Referenční třídy šablony musí být privátní. Mohou implementovat Obecná rozhraní a mohou předat parametr šablony *t* obecnému argumentu *t*. Každé vytvoření instance referenční třídy s šablonou je vlastní referenční třída.

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
