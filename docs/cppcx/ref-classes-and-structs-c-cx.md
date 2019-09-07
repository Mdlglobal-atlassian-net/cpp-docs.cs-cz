---
title: Ref Classes a structsC++(/CX)
ms.date: 01/22/2017
ms.assetid: 3d736b82-0bf0-48cf-bac1-cc9d110b70d1
ms.openlocfilehash: b58c5b64d8f4a60b418fdd2b11318055a8fb618e
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740889"
---
# <a name="ref-classes-and-structs-ccx"></a>Ref Classes a structsC++(/CX)

Třída C++/CX podporuje uživatelsky definované *referenční třídy* a *struktury ref*a uživatelsky definované *třídy hodnot* a *struktury hodnot*. Tyto datové struktury jsou primární kontejnery, podle kterých C++/CX podporuje systém typů prostředí Windows Runtime. Jejich obsah se generuje do metadat podle určitých specifických pravidel a umožňuje jejich předávání mezi prostředí Windows Runtime komponentami a Univerzální platforma Windowsmi aplikacemi, které jsou napsané v C++ nebo jiných jazycích.

Struktura ref class nebo ref má tyto základní funkce:

- Musí být deklarován v rámci oboru názvů, v oboru názvů a v tomto oboru názvů může mít veřejný nebo privátní přístupnost. Pouze veřejné typy jsou generovány do metadat. Vnořené definice veřejných tříd nejsou povolené, včetně vnořených veřejných tříd [Enum](../cppcx/enums-c-cx.md) . Další informace naleznete v části [obory názvů a viditelnost typů](../cppcx/namespaces-and-type-visibility-c-cx.md).

- Může obsahovat jako členy C++/CX, včetně ref Classes, hodnotových tříd, struktur odkazů, hodnotových struktur nebo struktur hodnot s možnou hodnotou null. Může také obsahovat skalární typy, například float64, bool a tak dále. Může obsahovat také standardní C++ typy, například `std::vector` nebo vlastní třídu, pokud nejsou veřejné. C++`public`Konstrukce/CX mohou mít přístup, `protected`, `internal`, `private`nebo `protected private` přístupnost. Všichni `public` členové `protected` nebo jsou vydáváni do metadat. Standardní C++ typy musí mít `private` `internal`přístup, nebo `protected private` přístupnost, což brání v jejich generování do metadat.

- Může implementovat jednu nebo více *tříd rozhraní* nebo *struktur*rozhraní.

- Může dědit z jedné základní třídy a samotné základní třídy mají další omezení. Dědičnost v hierarchiích veřejných referenčních tříd má více omezení než dědičnost v privátních referenčních třídách.

- Nemůže být deklarován jako obecný. Pokud má privátní přístupnost, může to být šablona.

- Jeho životnost je spravována automatickým počítáním odkazů.

## <a name="declaration"></a>Deklarace

Následující fragment kódu deklaruje `Person` třídu ref. Všimněte si, že C++ `std::map` standardní typ se používá v privátních členech a rozhraní`IMapView` prostředí Windows Runtime se používá ve veřejném rozhraní. Všimněte si také, že "^" je připojen k deklaracím typů odkazů.

[!code-cpp[cx_classes#03](../cppcx/codesnippet/CPP/classesstructs/class1.h#03)]

## <a name="implementation"></a>Implementace

Tento příklad kódu ukazuje implementaci `Person` referenční třídy:

[!code-cpp[cx_classes#04](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#04)]

## <a name="usage"></a>Použití

Následující příklad kódu ukazuje, `Person` jak kód klienta používá referenční třídu.

[!code-cpp[cx_classes#05](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#05)]

Můžete také použít sémantiku zásobníku k deklaraci místní proměnné ref class. Takový objekt se chová jako proměnná založená na zásobníku i v případě, že je paměť stále přidělena dynamicky. Jedním z důležitých rozdílů je, že nemůžete přiřadit sledovací odkaz (%) na proměnnou, která je deklarována pomocí sémantiky zásobníku; To zaručuje, že počet odkazů bude při ukončení funkce snížen na nulu. Tento příklad ukazuje základní referenční třídu `Uri`a funkci, která ji používá s sémantikou zásobníku:

[!code-cpp[cx_classes#06](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#06)]

## <a name="memory-management"></a>Správa paměti

Třídu ref class v dynamické paměti přidělíte pomocí `ref new` klíčového slova.

[!code-cpp[cx_classes#01](../cppcx/codesnippet/CPP/classesstructs/class1.h#01)]

Operátor Handle-to-Object ^ je známý jako "Hat" a je v C++ podstatě inteligentní ukazatel. Paměť, na kterou ukazuje, je automaticky zničena v případě, že poslední stříška překročí rozsah nebo `nullptr`je explicitně nastaven na.

Podle definice má ref class sémantiku reference. Při přiřazení proměnné třídy ref je popisovač, který je zkopírován, nikoli samotný objekt. V dalším příkladu po přiřazení obě `myClass` a `myClass2` odkazují na stejné umístění v paměti.

[!code-cpp[cx_classes#02](../cppcx/codesnippet/CPP/classesstructs/class1.h#02)]

Je- C++li vytvořena instance referenční třídy/CX, je před voláním konstruktoru inicializována jeho paměť. Proto není nutné inicializovat jednotlivé členy, včetně vlastností. Je- C++li třída/CX odvozena z třídy C++ knihovny prostředí Windows Runtime (WRL), je nulová C++inicializace pouze část odvozené třídy/CX.

### <a name="members"></a>Členové

`public`Referenční třída může obsahovat členy `private` funkce `protected`, a. pouze `public` `protected` členové jsou vydáváni do metadat. Vnořené třídy a třídy ref jsou povoleny, ale nemohou `public`být. Veřejná pole nejsou povolena; veřejné datové členy musí být deklarovány jako vlastnosti. Soukromý nebo chráněný interní datový člen může být pole. Ve výchozím nastavení je `private`v referenční třídě přístupnost všech členů.

Struktura ref je stejná jako ref class, s tím rozdílem, že ve výchozím nastavení mají `public` členové mít přístupnost.

Struktura `public` ref class nebo ref je generována v metadatech, ale je možné ji použít z jiných Univerzální platforma Windows aplikací a prostředí Windows Runtime komponent, které musí mít alespoň jeden veřejný nebo chráněný konstruktor. Veřejná referenční třída, která má veřejný konstruktor, musí být také deklarována `sealed` jako, aby se zabránilo dalšímu odvození prostřednictvím binárního rozhraní aplikace (ABI).

Veřejné členy nelze deklarovat jako const, protože systém typů prostředí Windows Runtime nepodporuje const. Můžete použít statickou vlastnost k deklaraci veřejného datového členu s konstantní hodnotou.

Při definování veřejné referenční třídy nebo struktury použije kompilátor požadované atributy na třídu a uloží tyto informace do souboru. winmd aplikace. Nicméně při definování veřejné nezapečetěné referenční třídy, ručně použijte `Windows::Foundation::Metadata::WebHostHidden` atribut, abyste zajistili, že třída není viditelná pro Univerzální platforma Windows aplikace, které jsou napsány v jazyce JavaScript.

Referenční C++ třída může mít standardní typy, včetně `const` typů `internal`, v jakémkoli `private`členu, nebo `protected private` .

Veřejné referenční třídy, které mají parametry typu, nejsou povoleny. Uživatelsky definované obecné referenční třídy nejsou povoleny. Soukromá, interní nebo chráněná soukromá referenční třída může být šablonou.

## <a name="destructors"></a>Destruktory

V C++/CX volání `delete` veřejného destruktoru vyvolá destruktor bez ohledu na počet odkazů objektu. Toto chování umožňuje definovat destruktor, který provede vlastní vyčištění neRAIIch prostředků deterministickým způsobem. Nicméně i v tomto případě není samotný objekt z paměti odstraněn. Paměť pro objekt je uvolněna pouze v případě, že počet odkazů dosáhne nuly.

Pokud destruktor třídy není veřejný, je vyvolána pouze v případě, že počet odkazů dosáhne nuly. Pokud voláte `delete` na objekt, který má privátní destruktor, kompilátor vyvolá upozornění C4493, což znamená, že "výraz DELETE nemá žádný vliv, protože \<destruktor typu Name > nemá přístupnost Public".

Destruktory ref class lze deklarovat pouze následujícím způsobem:

- veřejné a virtuální (povolené pro zapečetěné nebo nezapečetěné typy)

- chráněná soukromá a nevirtuální (povoluje se jenom pro nezapečetěné typy)

- privátní a nevirtuální (povolené jenom pro zapečetěné typy)

Žádná jiná kombinace možností usnadnění přístupu, virtualizace a zapečetění není povolená.  Pokud explicitně nedeklarujete destruktor, kompilátor vygeneruje veřejný virtuální destruktor, pokud základní třída typu nebo kterýkoli člen má veřejný destruktor. V opačném případě kompilátor vygeneruje chráněný privátní nevirtuální destruktor pro nezapečetěné typy nebo privátní nevirtuální destruktor pro zapečetěné typy.

Chování není definováno, pokud se pokusíte získat přístup ke členům třídy, které již mají spuštěný destruktor; pravděpodobně dojde k chybě programu. Volání `delete t` na typ, který nemá žádný veřejný destruktor, nemá žádný vliv. Volání `delete this` na typ nebo základní třídu, která má známý `private` nebo `protected private` destruktor z v rámci své hierarchie typů, nemá také žádný vliv.

Při deklaraci veřejného destruktoru kompilátor vygeneruje kód tak, aby třída ref class implementovala `Platform::IDisposable` a destruktor `Dispose` implementuje metodu. `Platform::IDisposable`je projekcí C++/CX pro `Windows::Foundation::IClosable`. Tato rozhraní nikdy Neimplementujte explicitně.

## <a name="inheritance"></a>Dědičnost

Platform:: Object je univerzální základní třída pro všechny třídy ref. Všechny třídy ref jsou implicitně převoditelné na Platform:: Object a můžou přepsat [Object:: ToString](../cppcx/platform-object-class.md#tostring). Model dědičnosti prostředí Windows Runtime však není určen jako obecný model dědičnosti; v C++/CX to znamená, že uživatelsky definovaná třída veřejné ref nemůže sloužit jako základní třída.

Pokud vytváříte uživatelský ovládací prvek XAML a objekt se účastní v systému vlastností závislosti, pak můžete použít `Windows::UI::Xaml::DependencyObject` jako základní třídu.

Po definování nezapečetěné třídy `MyBase` , která dědí z `DependencyObject`, jiné veřejné nebo soukromé třídy ref ve vaší komponentě nebo aplikaci mohou dědit z `MyBase`. Dědičnost ve veřejných referenčních třídách by měla být provedena pouze v případě, že bude podporovat přepsání virtuálních metod, polymorfní identity a zapouzdření.

Soukromá třída ref class není vyžadována pro odvození z existující nezapečetěné třídy. Pokud vyžadujete, aby hierarchie objektu mohla modelovat vlastní strukturu programu nebo povolit opakované použití kódu, použijte soukromé nebo interní referenční třídy nebo ještě lepší, standardní C++ třídy. Funkci hierarchie privátních objektů můžete vystavit prostřednictvím veřejné obálky zapečetěné referenční třídy.

Referenční třída, která má veřejný nebo chráněný konstruktor v C++/CX, musí být deklarována jako Sealed. Toto omezení znamená, že neexistuje žádný způsob, jak třídy, které jsou zapsány v C# jiných jazycích, například nebo Visual Basic, k dědění z typů, které deklarujete v C++komponentě prostředí Windows Runtime, která je napsána v/CX.

Tady jsou základní pravidla dědičnosti v C++/CX:

- Třídy ref mohou dědit přímo z jedné základní referenční třídy, ale mohou implementovat libovolný počet rozhraní.

- Pokud má třída veřejný konstruktor, musí být deklarována jako Sealed, aby nedocházelo k dalšímu odvození.

- Můžete vytvořit veřejné nezapečetěné základní třídy, které mají interní nebo chráněné soukromé konstruktory za předpokladu, že základní třída je odvozena přímo nebo nepřímo z existující nezapečetěné základní třídy, `Windows::UI::Xaml::DependencyObject`jako je například. Dědičnost uživatelsky definovaných referenčních tříd napříč soubory. winmd není podporována. Třída ref class však může dědit z rozhraní, které je definováno v jiném souboru winmd. Můžete vytvořit odvozené třídy z uživatelsky definované základní referenční třídy pouze v rámci stejné prostředí Windows Runtime komponenty nebo Univerzální platforma Windows aplikace.

- Pro třídy ref jsou podporovány pouze veřejné dědění.

   [!code-cpp[cx_classes#08](../cppcx/codesnippet/CPP/classesstructs/class1.h#08)]

Následující příklad ukazuje, jak vystavit veřejnou referenční třídu, která je odvozena z jiných referenčních tříd v hierarchii dědičnosti.

[!code-cpp[cx_classes#09](../cppcx/codesnippet/CPP/classesstructs/class1.h#09)]

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Hodnotové třídy a struktury](../cppcx/value-classes-and-structs-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
