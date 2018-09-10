---
title: Referenční třídy a struktury (C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3d736b82-0bf0-48cf-bac1-cc9d110b70d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e38b57fbdf5c6e815f4e099c7cb7d37674799877
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101739"
---
# <a name="ref-classes-and-structs-ccx"></a>Referenční třídy a struktury (C + +/ CX)

C + +/ CX podporuje uživatelem definované *referenční třídy* a *struktury ref*a uživatelem definovanými *hodnota třídy* a *hodnotu struktury*. Tyto datové struktury jsou primární kontejnery, ve které C + +/ CX podporuje systém typů prostředí Windows Runtime. K metadatům podle určité zvláštní pravidla jsou emitovány jejich obsah a díky tomu mají být předány mezi komponentami prostředí Windows Runtime a aplikací pro univerzální platformu Windows, které jsou napsány v C++ nebo jiných jazycích.

Třída ref class nebo ref struct má tyto základní funkce:

- Musí být deklarována v rámci oboru názvů v oboru názvů, a v tomto oboru názvů může mít přístupnost veřejné nebo soukromé. Pouze veřejné typy jsou emitovány do metadat. Není povoleno definovat vnořené veřejnou třídu, včetně vnořený veřejný [výčtu](../cppcx/enums-c-cx.md) třídy. Další informace najdete v tématu [obory názvů a viditelnost typů](../cppcx/namespaces-and-type-visibility-c-cx.md).

- Může obsahovat jako členy C + +/ CX včetně referenční třídy, hodnota třídy, struktury ref, struktuře hodnot nebo struktury s možnou hodnotou Null. Může také obsahovat Skalární typy, jako jsou float64, bool a tak dále. Standardní typy jazyka C++ může také obsahovat například `std::vector` nebo vlastní třídu, dokud nejsou veřejné. C + +/ CX konstrukce pravděpodobně `public`, `protected`, `internal`, `private`, nebo `protected private` usnadnění přístupu. Všechny `public` nebo `protected` členy jsou emitovány do metadat. Standardní C++ typy musí mít `private`, `internal`, nebo `protected private` usnadnění, které brání právě emituje do metadat.

- Může implementovat jednu nebo více *rozhraní třídy* nebo *rozhraní struktury*.

- Může dědit z jedné základní třídy a samotné základní třídy mají další omezení. Dědičnost v hierarchiích třída public ref má více omezení než dědičnosti v privátní referenční třídy.

- Nemůže deklarovat jako obecný. Pokud má přístupnost private, může být šablonou.

- Jeho životnost se spravuje přes Automatické počítání odkazů.

## <a name="declaration"></a>Deklarace

Následující fragment kódu deklaruje `Person` třídy ref class. Všimněte si, že standardní C++ `std::map` typ se používá v soukromé členy a prostředí Windows Runtime`IMapView` rozhraní se používá ve veřejném rozhraní. Všimněte si také, že "^" se připojí k deklarace odkazů.

[!code-cpp[cx_classes#03](../cppcx/codesnippet/CPP/classesstructs/class1.h#03)]

## <a name="implementation"></a>Implementace

Tento příklad kódu ukazuje implementaci `Person` referenční třídy:

[!code-cpp[cx_classes#04](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#04)]

## <a name="usage"></a>Použití

Následující příklad kódu ukazuje, jak kód klienta používá `Person` třídy ref class.

[!code-cpp[cx_classes#05](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#05)]

Můžete také sémantika zásobníku pro deklarování proměnné třídy lokálního odkazu. Takový objekt se chová jako proměnnou založenou na zásobníku, i v případě, že stále přidělení dynamické paměti. Jeden důležitý rozdíl je, že nemůžete přiřadit sledovacího odkazu (%) proměnné, která je deklarována pomocí – sémantika zásobníku; zaručí se tak, že je počet odkazů sníží na nulu, když funkce skončí. Tento příklad ukazuje základní referenční třídy `Uri`a funkce, která se používá s – sémantika zásobníku:

[!code-cpp[cx_classes#06](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#06)]

## <a name="memory-management"></a>Správa paměti

Přidělit referenční třídy v dynamické paměti pomocí `ref new` – klíčové slovo.

[!code-cpp[cx_classes#01](../cppcx/codesnippet/CPP/classesstructs/class1.h#01)]

Operátor popisovače objektu ^ se označuje jako "hat" a je v podstatě C++ inteligentního ukazatele. Odkazuje na paměť je automaticky zničen při poslední hat dostane mimo rozsah nebo je explicitně nastaveno na `nullptr`.

Podle definice třídy ref class má sémantiku odkazu. Když přiřadíte referenční třídy proměnné, je popisovač, který se má zkopírovat, nikoli samotného objektu. V následujícím příkladu, po přiřazení oba `myClass` a `myClass2` odkazovat na stejné místo v paměti.

[!code-cpp[cx_classes#02](../cppcx/codesnippet/CPP/classesstructs/class1.h#02)]

Když C + +/ CX referenční třídy je vytvořena instance, jeho paměti je inicializována nulou před voláním konstruktoru; proto není nutné pro jednotlivé členy, včetně vlastnosti inicializace nula. Pokud C + +/ CX třída odvozena z třídy Windows Runtime C++ knihovny (WRL), pouze jazyce C + +/ CX odvozená třída je inicializována nulou.

### <a name="members"></a>Členové

Třídy ref class. může obsahovat `public`, `protected`, a `private` funkce členy; pouze `public` a `protected` členy se emitovat do metadat. Vnořené třídy a třídy ref nejsou povoleny, ale není možné `public`. Veřejná pole nejsou povolené; veřejné datové členy musí být deklarována jako vlastnosti. Pole může být soukromé nebo chráněné vnitřní datové členy. Ve výchozím nastavení v referenční třídě přístupnost všech členů je `private`.

Ref struct je stejná jako třída ref, s tím rozdílem, že ve výchozím nastavení mají jeho členové `public` usnadnění přístupu.

A `public` ref class nebo ref struct je vygenerován v metadatech, ale chcete-li možné použít z jiných aplikací pro univerzální platformu Windows a součásti prostředí Windows Runtime musí mít aspoň jeden veřejný nebo chráněný konstruktor. Třída public ref class, která má veřejný konstruktor musí být také deklarovány jako `sealed` aby se zabránilo dalším odvození prostřednictvím binárním rozhraním aplikace (ABI).

Veřejné členy se nedá deklarovat jako const protože systém typů prostředí Windows Runtime nepodporuje const. Statická vlastnost můžete použít k deklarování člena veřejná data s konstantní hodnotou.

Při definování třída public ref class nebo struct, kompilátor platí povinné atributy pro třídu a ukládá tyto informace v souboru .winmd aplikace. Nicméně, když definujete veřejné nezapečetěná třída ref class, aplikovat ručně `Windows::Foundation::Metadata::WebHostHidden` atribut Ujistěte se, že třída není viditelné pro aplikace univerzální platformy Windows, které jsou napsány v jazyce JavaScript.

Referenční třída může mít standardní typy jazyka C++, včetně `const` typy v libovolném `private`, `internal`, nebo `protected private` členy.

Veřejné referenční třídy, které má parametry typu nejsou povolené. Uživatelem definované Obecné referenční třídy nejsou povoleny. Soukromé, interní nebo chráněné privátním referenční třídy mohou být šablonou.

## <a name="destructors"></a>Destruktory

V jazyce C + +/ CX, volání `delete` na veřejným destruktorem vyvolá destruktor bez ohledu na počet odkazů na objekt. Toto chování umožňuje definovat destruktor, který provede vlastní vyčištění prostředků – vzoru RAII deterministické způsobem. I v tomto případě není však samotný objekt odstraněn z paměti. Paměť pro objekt je uvolněna pouze při počet odkazů dosáhne nuly.

Pokud destruktor třídy nejsou veřejné, pak je pouze vyvoláno, když počet odkazů dosáhne nuly. Při volání `delete` na objekt, který má privátní destruktor, kompilátor vyvolá upozornění C4493, který říká "odstranit výraz nemá žádný účinek, jako je destruktor \<název typu > nemá přístupnost public.."

Destruktory třídy REF se dají deklarovat jenom následujícím způsobem:

- veřejné a virtuální (povolená v zapečetěné nebo nezapečetěné typy)

- chránit soukromý i nevirtuální (pouze povolené pro nezapečetěné typy)

- privátní a nevirtuální (povolena pouze v zapečetěných typech)

Žádné jiné kombinace přístupnost, virtualness a sealedness se nepovoluje.  Pokud můžete explicitně destruktor nedeklaruje, kompilátor vygeneruje veřejný virtuální destruktor, pokud veřejným destruktorem základní třídy typ nebo člena. V opačném případě kompilátor generuje chráněné privátním nevirtuální destruktor pro nezapečetěné typy nebo privátní nevirtuální destruktor pro zapečetěné typy.

Chování není definováno, pokud se pokusíte pro přístup ke členům třídy, která již byla jeho destruktor spuštění. pravděpodobně způsobí pád programu. Volání `delete t` na typ, který nemá žádný destruktor public nemá žádný vliv. Volání `delete this` na typ nebo základní třídu, která obsahuje známou `private` nebo `protected private` destruktor z v rámci své hierarchie typů také nemá žádný vliv.

Když deklarujete veřejným destruktorem, kompilátor generuje kód tak, aby třída ref implementuje `Platform::IDisposable` a implementuje destruktor `Dispose` metody. `Platform::IDisposable` je C + +/ CX projekci `Windows::Foundation::IClosable`. Tato rozhraní implementují nikdy explicitně.

## <a name="inheritance"></a>Dědičnost

Platform::Object – je univerzální základní třída pro všechny třídy ref. Všechny referenční třídy jsou implicitně převést na Platform::Object – a můžete přepsat [Object::ToString](../cppcx/platform-object-class.md#tostring). Ale model dědičnosti modulu Windows Runtime nejsou určeny jako obecné model dědičnosti; v jazyce C + +/ CX, to znamená, že uživatelský public ref class nemůže sloužit jako základní třídu.

Pokud se vytvoření uživatelského ovládacího prvku XAML a účastní v systému vlastností závislosti, pak můžete použít `Windows::UI::Xaml::DependencyObject` jako základní třídu.

Po definování nezapečetěné třídy `MyBase` , která dědí z `DependencyObject`, v komponentě třídy ref jiných veřejných nebo privátních nebo aplikace může dědit z `MyBase`. Dědičnost v veřejné referenční třídy lze provádět pouze pro podporu přepsání virtuální metody, polymorfní identity a zapouzdření.

Privátní base ref class není nutné odvozovat od existující nezapečetěné třídy. Pokud potřebujete hierarchii objektů modelu strukturu programu nebo povolit opakované využívání kódu, použijte privátní nebo interní referenční třídy nebo ještě lépe, standardní třídy jazyka C++. Můžete zveřejnit funkčnost privátní objekt hierarchie prostřednictvím obálky třída public ref zapečetěné.

Ref class, která má veřejný nebo chráněný konstruktor v jazyce C + +/ CX musí být deklarované jako sealed. Toto omezení znamená, že neexistuje žádný způsob, jak třídy, které jsou napsané v jiných jazycích, jako je C# nebo Visual Basic pro dědění z typů, které deklarujete v součásti prostředí Windows Runtime, která je napsána v jazyce C + +/ CX.

Tady jsou základní pravidla dědičnosti v C + +/ CX:

- Referenční třídy lze dědit přímo z nejvýše jedna základní třída ref class, ale může implementovat libovolný počet rozhraní.

- Pokud třída nemá veřejný konstruktor, musí být deklarován jako zapečetěný, aby se zabránilo dalším odvození.

- Můžete vytvořit veřejnou nezapečetěné základních tříd, které mají interní nebo chráněné soukromé konstruktory, za předpokladu, že základní třídy je odvozen přímo nebo nepřímo z existující nezapečetěný základní třídy, jako `Windows::UI::Xaml::DependencyObject`. Dědičnost tříd ref uživatelem definované napříč soubory .winmd není podporována. třídy ref class však může dědit z rozhraní, která je definována v jiném souboru .winmd. Odvozené třídy můžete vytvořit z uživatelem definované základní referenční třídy pouze v rámci stejné komponenty prostředí Windows Runtime nebo aplikace pro univerzální platformu Windows.

- Pro referenční třídy je podporována pouze veřejné dědičnost.

   [!code-cpp[cx_classes#08](../cppcx/codesnippet/CPP/classesstructs/class1.h#08)]

Následující příklad ukazuje, jak vystavit třída public ref class, která je odvozena od jiné referenční třídy v hierarchii dědičnosti.

[!code-cpp[cx_classes#09](../cppcx/codesnippet/CPP/classesstructs/class1.h#09)]

## <a name="see-also"></a>Viz také

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Hodnota třídy a struktury](../cppcx/value-classes-and-structs-c-cx.md)<br/>
[Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)