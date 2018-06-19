---
title: REF třídy a struktury (C + +/ CX) | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3d736b82-0bf0-48cf-bac1-cc9d110b70d1
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: be0a8adbb2bf20e4f92edf16fa2217a7d2b40eab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092441"
---
# <a name="ref-classes-and-structs-ccx"></a>REF třídy a struktury (C + +/ CX)
C + +/ CX podporuje uživatelem definované *ref třídy* a *ref struktury*a uživatelem definovanými *hodnota třídy* a *hodnota struktury*. Tyto datové struktury jsou primární kontejnery, které C + +/ CX podporuje systém typů prostředí Windows Runtime. K metadatům podle určité konkrétní pravidla jsou vygenerované jejich obsah, a díky tomu mohou být předán mezi součástmi prostředí Windows Runtime a univerzální platformu Windows aplikace, které jsou zapsány v C++ nebo jiných jazyků.  
  
 Ref třídě nebo struktuře ref má tyto základní funkce:  
  
-   Musí být deklarován v oboru názvů, v oboru názvů, a v daném oboru názvů pravděpodobně veřejných nebo privátních usnadnění. Pouze veřejné typy jsou vydávány na metadata. Definice veřejné vnořené třídy nejsou povoleny, včetně vnořené veřejné [výčtu](../cppcx/enums-c-cx.md) třídy. Další informace najdete v tématu [obory názvů a viditelnost typů](../cppcx/namespaces-and-type-visibility-c-cx.md).  
  
-   Může obsahovat jako členy C + +/ CX včetně ref třídy, hodnota třídy, struktury ref, hodnota struktury nebo struktury hodnot hodnotu Null. Může také obsahovat Skalární typy, jako je například float64, bool a tak dále. Standardní typy C++ může obsahovat také jako `std::vector` nebo vlastní třídy, pokud nejsou veřejné. C + +/ CX konstrukce může mít `public`, `protected`, `internal`, `private`, nebo `protected private` usnadnění. Všechny `public` nebo `protected` členové jsou vygenerované na metadata. Standardní typy C++ musí mít `private`, `internal`, nebo `protected private` usnadnění, což zabrání se vygenerované na metadata.  
  
-   Může implementovat, jeden nebo více *rozhraní třídy* nebo *rozhraní struktury*.  
  
-   Mohou dědit z jedné základní třídy a třídy base sami mají další omezení. Dědičnost v hierarchie tříd veřejné ref má další omezení než dědičnosti v privátní ref třídy.  
  
-   Nemusí deklarována jako obecný. Pokud má privátní usnadnění, může být šablonu.  
  
-   Celé jeho životnosti spravuje počítání automatické odkazů.  
  
## <a name="declaration"></a>Deklarace  
 Následující fragment kódu deklaruje `Person` ref třídy. Všimněte si, že standardní C++ `std::map` typ se používá v soukromé členy a prostředí Windows Runtime`IMapView` rozhraní se používá v veřejné rozhraní. Všimněte si také, že "^" se připojuje k deklarace odkazové typy.  
  
 [!code-cpp[cx_classes#03](../cppcx/codesnippet/CPP/classesstructs/class1.h#03)]  
  
## <a name="implementation"></a>Implementace  
 Tento příklad kódu ukazuje implementaci `Person` ref třídy:  
  
 [!code-cpp[cx_classes#04](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#04)]  
  
## <a name="usage"></a>Použití  
 Další příklad kódu ukazuje, jak kód klienta používá `Person` ref třídy.  
  
 [!code-cpp[cx_classes#05](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#05)]  
  
 Můžete taky sémantika zásobníku deklarovat proměnné třídy místní ref. Přestože paměť je pořád ještě přidělená dynamicky, se chová jako proměnné založené na zásobníku takového objektu. Jeden důležitý rozdíl je, že sledovací odkaz (%) nelze přiřadit do proměnné, která je deklarovaný s použitím sémantika zásobníku; to zaručuje, že počet odkazů se odečte nule při ukončení funkce. Tento příklad ukazuje třídu základní ref `Uri`a funkce, která používá s sémantika zásobníku:  
  
 [!code-cpp[cx_classes#06](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#06)]  
  
## <a name="memory-management"></a>Správa paměti  
 Přidělit ref třídu v dynamické paměti pomocí `ref new` – klíčové slovo.  
  
 [!code-cpp[cx_classes#01](../cppcx/codesnippet/CPP/classesstructs/class1.h#01)]  
  
 Operátor popisovače objektu ^ je známý jako "hat" a je zásadně inteligentní ukazatel C++. Při poslední hat ocitne mimo rozsah, nebo je explicitně nastaven na automaticky zničena paměti odkazuje `nullptr`.  
  
 Podle definice třídy ref má sémantiku odkaz. Přiřadíte-li třídu ref proměnné, je popisovač, který byl zkopírován, není objekt. V následujícím příkladu, po přiřazení obě `myClass` a `myClass2` bodu do stejného umístění paměti.  
  
 [!code-cpp[cx_classes#02](../cppcx/codesnippet/CPP/classesstructs/class1.h#02)]  
  
 Když C + +/ CX ref třída je vytvořena instance, jeho paměti je nula inicializovat před jeho konstruktoru nazývá; proto není potřeba nula inicializovat jednotlivé členy, včetně vlastnosti. Pokud jazyce C + +/ CX třída odvozena od třídy Windows knihovny pro C++ Runtime (WRL), pouze jazyce C + +/ CX odvozené třídy část je inicializován nula.  
  
### <a name="members"></a>Členové  
 Ref třída obsahovat `public`, `protected`, a `private` funkce členy; pouze `public` a `protected` členové jsou vložen do metadat. Vnořené třídy a třídy ref jsou povolené, ale nemůže být `public`. Veřejná pole nejsou povoleny; veřejná data členů musí být deklarován jako vlastnosti. Pole může být privátní nebo chráněného interních datových členů. Ve výchozím nastavení v třídě ref, usnadnění všech členů je `private`.  
  
 Ref struct je stejná jako třída ref, s tím rozdílem, že ve výchozím nastavení mají její členy `public` usnadnění.  
  
 A `public` ref třídě nebo struktuře ref jsou vydávány v metadatech, ale chcete-li možné použít z jiných aplikací pro univerzální platformu Windows a prostředí Windows Runtime součásti musí mít alespoň jeden veřejný nebo chráněný konstruktor. Veřejné ref třídy, která má konstruktor public, který musí být také deklarována jako `sealed` aby se zabránilo dalším odvození přes rozhraní binární aplikace (ABI).  
  
 Veřejné členy nemusí být deklarován jako const protože systém typů prostředí Windows Runtime nepodporuje const. Můžete pomocí statické vlastnosti deklarovat veřejná data člena s konstantní hodnotou.  
  
 Když definujete veřejné ref třídě nebo struktuře, kompilátor povinné atributy se vztahuje na třídu a ukládá tyto informace v souboru .winmd aplikace. Ale když můžete definovat třídu veřejné nezapečetěných ref, ručně použít `Windows::Foundation::Metadata::WebHostHidden` atribut zajistit, že třída není viditelná pro univerzální platformu Windows aplikace, které jsou napsané v jazyce JavaScript.  
  
 Třída ref může mít standardní typy C++, včetně `const` typy v žádném `private`, `internal`, nebo `protected private` členy.  
  
 Veřejné ref tříd, které mají parametry typu nejsou povoleny. Uživatelem definované obecné ref třídy nejsou povoleny. Soukromé, interní nebo chráněné privátním ref třída může být šablonu.  
  
## <a name="destructors"></a>Destruktory  
 V jazyce C + +/ CX, volání `delete` na veřejné destruktor vyvolá destruktor bez ohledu na počet odkazů objektu. Toto chování umožňuje definovat destruktor, která provádí vlastní vyčištění prostředků jiný RAII deterministickou způsobem. I v tomto případě se ale samotného objektu neodstraní z paměti. Pokud počet odkazů hodnota nula, je pouze uvolnit paměť pro objekt.  
  
 Pokud není veřejný destruktor třídy a, pak jej je volána, pouze když počet odkazů hodnota nula. Když zavoláte `delete` na objekt, který má privátní destruktor, kompilátor vyvolá upozornění C4493, s informacemi o tom "odstranit výraz nemá žádný účinek jako destruktoru objektu \<název typu > nemá usnadnění 'veřejné'."  
  
 Destruktory třídy REF lze deklarovat pouze následujícím způsobem:  
  
-   veřejné a virtuální (povolena na zapečetěné nebo nezapečetěné typy)  
  
-   chráněné privátní a bez virtuální (pouze povolené na nezapečetěných typy)  
  
-   privátní a nevirtuálních (povolena pouze v zapečetěných typech)  
  
 Žádné jiné kombinace usnadnění, virtualness a sealedness je povolena.  Pokud destruktor není explicitně deklarovat, kompilátor vygeneruje veřejné virtuální destruktor, pokud základní třídy typ nebo libovolný člen má veřejné – destruktor. Kompilátor, jinak hodnota generuje chráněné privátní nevirtuálních destruktor pro nezapečetěných typy nebo privátní nevirtuálních destruktor pro zapečetěných typech.  
  
 Toto chování je definován, pokud se pokusíte přístup ke členům třídy, která má jeho destruktor spustit; může to způsobit s největší pravděpodobností program, který má havárie. Volání metody `delete t` na typ, který nemá žádný veřejný destruktor nemá žádný vliv. Volání metody `delete this` na typ nebo základní třída, která má známá `private` nebo `protected private` – destruktor v rámci jeho typ hierarchie taky nemá žádný vliv.  
  
 Po deklarování veřejné destruktor kompilátor generuje kód tak, aby ref třída implementuje `Platform::IDisposable` a implementuje destruktor `Dispose` metoda. `Platform::IDisposable` je C + +/ CX projekci `Windows::Foundation::IClosable`. Implementovat nikdy explicitně tato rozhraní.  
  
## <a name="inheritance"></a>Dědičnost  
 Platform::Object je univerzální základní třídu pro všechny třídy ref. Všechny třídy ref jsou implicitně převést na Platform::Object a můžete přepsat [Object::ToString](../cppcx/platform-object-class.md#tostring). Však model dědičnosti prostředí Windows Runtime nejsou určené jako obecné model dědičnosti; v jazyce C + +/ CX, to znamená, že třídu uživatelem definované veřejné ref nemůže sloužit jako základní třídu.  
  
 Pokud vytváříte uživatelského ovládacího prvku XAML a účastní v systému vlastnost závislosti, pak můžete použít `Windows::UI::Xaml::DependencyObject` jako základní třída.  
  
 Po definování třídu nezapečetěné `MyBase` který dědí z `DependencyObject`, jiné veřejné nebo soukromé ref třídy v příslušné součásti nebo aplikace mohou dědit z `MyBase`. Dědičnost v třídách veřejné ref lze provádět pouze pro podporu přepsání virtuální metody, polymorfní identity a zapouzdření.  
  
 Privátní ref základní třída není nutné odvozovat z existující nezapečetěné třídy. Pokud budete potřebovat k hierarchii objektu modelu struktury programu nebo povolit opakované použití kódu, používat privátní nebo interní ref třídy nebo ještě lepší standardní třídy jazyka C++. Můžete vystavit funkci hierarchie soukromý objekt prostřednictvím veřejné ref zapečetěné třídy obálku.  
  
 Ref třídy, která má konstruktor veřejných nebo chráněné v jazyce C + +/ CX musí být deklarován jako zapečetěné. Toto omezení znamená, že neexistuje žádný způsob pro třídy, které jsou zapsány v jiných jazycích, jako je například C# nebo Visual Basic pro dědění z typů, které je deklarovat v prostředí Windows Runtime komponenty, která je napsán v jazyce C + +/ CX.  
  
 Zde jsou základní pravidla pro dědičnosti v jazyce C + +/ CX:  
  
-   REF třídy přímo z maximálně jeden ref základní třídy lze dědit, ale můžete implementovat libovolný počet rozhraní.  
  
-   Pokud třída má veřejný konstruktor, musí být deklarován jako zapečetěné, aby se zabránilo dalším odvození.  
  
-   Můžete vytvořit veřejné nezapečetěných základní třídy, které mají interní nebo chráněného soukromé konstruktory, za předpokladu, že základní třída odvozena přímo nebo nepřímo z existující nezapečetěné základní třídy, jako `Windows::UI::Xaml::DependencyObject`. Dědičnost třídy ref uživatelem definované v souborech .winmd nepodporuje; však ref třídy lze dědit z rozhraní, která je definována v jiném souboru .winmd. Můžete vytvořit odvozené od třídy, uživatelem definované základní ref pouze v rámci stejné komponenty prostředí Windows Runtime nebo aplikaci pro univerzální platformu Windows.  
  
-   Ref třídy je podporováno pouze veřejné dědičnosti.  
  
     [!code-cpp[cx_classes#08](../cppcx/codesnippet/CPP/classesstructs/class1.h#08)]  
  
 Následující příklad ukazuje, jak vystavit veřejné ref třídu, která pochází z jiné třídy ref v hierarchii dědičnosti.  
  
 [!code-cpp[cx_classes#09](../cppcx/codesnippet/CPP/classesstructs/class1.h#09)]  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)   
 [Hodnota třídy a struktury](../cppcx/value-classes-and-structs-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)