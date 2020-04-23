---
title: Přidání vlastnosti
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.prop.overview
- vc.codewiz.prop.idlattributes
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
- names, add property wizard
- IDL attributes, add property wizard
- stock properties, about stock properties
- stock properties
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
ms.openlocfilehash: 79b05fde362a44453aac45aa8dc269c9689ea8fc
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751184"
---
# <a name="add-a-property"></a>Přidání vlastnosti

Pomocí průvodce [přidáním vlastností](#names-add-property-wizard) můžete přidat metodu do rozhraní v projektu.

**Přidání vlastnosti k objektu:**

1. V [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code)klepněte pravým tlačítkem myši na název rozhraní, do kterého chcete vlastnost přidat.

   > [!NOTE]
   > Můžete také přidat vlastnosti dispinterfaces, které, pokud projekt je přiřazen, jsou vnořeny v uzlu knihovny.

1. V místní nabídce zvolte **Přidat**a pak **zvolte Přidat vlastnost**.

1. V [průvodci přidáním vlastnosti](#names-add-property-wizard)zadejte informace o vytvoření vlastnosti.

1. Na stránce [atributů IDL](#idl-attributes-add-property-wizard) průvodce zadejte nastavení jazyka idl (Interface Definition Language) (IDL).

1. Chcete-li přidat vlastnost, vyberte **Dokončit.**

A `Get` `Put` metody vlastnosti jsou zobrazeny jako dvě ikony v zobrazení třídy, pod rozhraním, kde je definována. Poklepáním na ikonu můžete zobrazit deklaraci vlastnosti v souboru IDL.

- Pro rozhraní KNIHOVNY `Get` ATL jsou funkce a `Put` přidány do souboru CPP a do souboru H jsou přidány odkazy na tyto funkce.

- Pro dispinterfaces knihovny MFC, pokud vyberete **členské proměnné** jako typ implementace, metoda a proměnná jsou přidány do třídy, která ji implementuje. Pokud vyberete **Get/Set metody** jako typ implementace, dvě metody jsou přidány do třídy, která ji implementuje.

## <a name="in-this-section"></a>V tomto oddílu

- [Jména, průvodce přidáním vlastností](#names-add-property-wizard)
- [Atributy IDL, Průvodce přidáním vlastností](#idl-attributes-add-property-wizard)
- [Skladové nemovitosti](#stock-properties)

## <a name="names-add-property-wizard"></a>Jména, průvodce přidáním vlastností

Tento průvodce slouží k přidání vlastnosti do rozhraní.

- **Typ vlastnosti**

  Nastaví typ vlastnosti, kterou přidáváte. Pro rozhraní dispinterfaces knihovny MFC zadejte vlastní typ nebo vyberte z předdefinovaného seznamu. Pokud zadáte burzovní implementaci vlastnosti, **typ vlastnosti** je nastaven na typ zásoby a není k dispozici pro změnu.

- **Název vlastnosti**

  Nastaví název vlastnosti. Pro rozhraní mfc disp, která jsou přidružena k ovládacím prvkům ActiveX, můžete zadat vlastní název nebo můžete vybrat název vlastnosti zásob z předdefinovaného seznamu. Pokud zadáte vlastní název vlastnosti, typ implementace **na skladě** není k dispozici. Popis vlastností v seznamu naleznete v [části Vlastnosti zásob.](#stock-properties)

  |Typ rozhraní|Popis|
  |--------------------|-----------------|
  |Duální rozhraní ATL, vlastní rozhraní a místní vlastní rozhraní|Zadejte název vlastnosti.|
  |Rozhraní dispinterface knihovny MFC, rozhraní pro potlačení ovládacího prvku ActiveX knihovny MFC|Zadejte název vlastnosti nebo vyberte vlastnost akcií ze seznamu. Pokud vyberete vlastnost ze seznamu, příslušná hodnota se zobrazí v poli **Typ vlastnosti.** Tento typ můžete změnit v závislosti na výběru v části **Typ implementace**.|

- **Návratový typ**

  Pouze rozhraní KNIHOVNY ATL. Nastaví návratový typ vlastnosti. Pro duální `HRESULT` rozhraní je vždy návratový typ a toto pole není k dispozici. Pro vlastní rozhraní můžete vybrat návratový typ ze seznamu. `HRESULT`je stále doporučeno, protože poskytuje standardní způsob vrácení chyb.

- **Název proměnné**

  Pouze rozhraní mfc disp. K dispozici pouze v případě, že zadáte **proměnnou Member** v části **Typ implementace**. Nastaví název členské proměnné, ke které je vlastnost přidružena. Ve výchozím nastavení je název `m_`proměnné nastaven na *Název_vlastností PropertyName*. Tento název můžete upravit.

- **Oznamovací funkce**

  Pouze rozhraní mfc disp. K dispozici pouze v případě, že zadáte **proměnnou Member** v části **Typ implementace**. Nastaví název funkce oznámení volané, pokud se změní vlastnost. Ve výchozím nastavení je název funkce `On`oznámení nastaven na *PropertyName*`Changed`. Tento název můžete upravit.

- **Funkce Get**

  Pro rozhraní mfc disp. K dispozici pouze v případě, že zadáte **Get/Set metody** v části **Typ implementace**. Nastaví název funkce pro získání vlastnosti. Ve výchozím nastavení je `Get` název funkce `Get`nastaven na *PropertyName*. Tento název můžete upravit. Pokud odstraníte název, funkce [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) je vložena do mapy odeslání rozhraní. Funkce `Get` *PropertyName* určuje, že vlastnost je čitelná.

- **Nastavit funkci**

  Pouze rozhraní mfc disp. K dispozici pouze v případě, že zadáte **Get/Set metody** v části **Typ implementace**. Nastaví název funkce pro nastavení vlastnosti. Ve výchozím nastavení je `Set` název funkce `Set`nastaven na *PropertyName*. Tento název můžete upravit. Pokud odstraníte název, funkce [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) je vložena do mapy odeslání rozhraní. Funkce `Set` *PropertyName* určuje, že vlastnost je zapisovatelná.

- **Typ implementace**

  Pouze rozhraní mfc disp. Určuje způsob implementace vlastnosti, kterou přidáváte.

  |Typ implementace|Popis|
  |-------------------------|-----------------|
  |**Akcií**|Určuje implementaci zásob pro vlastnost vybranou v **názvu vlastnosti**. Výchozí nastavení Další informace naleznete v [tématu vlastnosti zásob](#stock-properties).<br /><br /> Pokud zadáte **Stock**, pak **typ vlastnosti**, **Typ parametru**a **Název parametru** jsou ztlumené.|
  |**Členská proměnná**|Určuje, že vlastnost je přidána jako členská proměnná. Jako členské proměnné můžete přidat vlastní vlastnosti nebo většinu vlastností zásob. Nelze zadat **proměnnou Člen** `Caption`pro `hWnd`vlastnosti , a `Text` vlastnosti.<br /><br /> Poskytuje výchozí názvy v části **Název proměnné** a **funkce Oznámení**. Tento název můžete upravit.|
  |**Metody get/set**|Určuje, že vlastnost `Get`je ve `Set`výchozím nastavení přidána jako funkce *PropertyName* a *PropertyName.* Tyto názvy se zobrazí v části **Get funkce** a **Nastavit funkce**.<br /><br /> Můžete změnit výchozí **typ vlastnosti**, který předá hodnotu funkce Get. Můžete zadat parametry `Get` pro `Set` funkce a.|

- **Funkce Get**

  Pro rozhraní KNIHOVNY ATL. Nastaví vlastnost jako čitelnou; to znamená, že `Get` vytvoří metodu pro načítání této vlastnosti z objektu. Vyberte **Získat**, **Put**nebo obojí.

- **Funkce Put**

  Pouze rozhraní KNIHOVNY ATL. Nastaví vlastnost zapisovatelnou; to znamená, že `Put` vytvoří metodu pro nastavení nebo "putting", tuto vlastnost objektu. Vyberte **Získat**, **Put**nebo obojí. Pokud vyberete tuto možnost, můžete si vybrat z následujících dvou způsobů implementace metody:

  |Možnost|Popis|
  |------------|-----------------|
  |**PropPut**|Funkce [PropPut](../windows/propput.md) vrátí kopii objektu. Toto je výchozí a nejběžnější způsob, jak vlastnost zapisovat.|
  |**Propputref**|Funkce [PropPutRef](../windows/propputref.md) vrátí odkaz na objekt, nikoli vrácení kopie samotného objektu. Zvažte použití této možnosti pro objekty, jako jsou velké struktury nebo pole, které mohou mít inicializační režii.|

- **Atributy parametru**

  Pouze rozhraní KNIHOVNY ATL. Určuje, zda je `in`parametr určený `out` **názvem parametru** , , obojí nebo žádný.

  |Možnost|Popis|
  |------------|-----------------|
  |`in`|Označuje, že parametr je předán z volající procedury do volané procedury.|
  |`out`|Označuje, že parametr ukazatele je vrácena z volané procedury volající procedury (ze serveru do klienta).|

- **Typ parametru**

  Nastaví datový typ parametru. Vyberte typ ze seznamu.

- **Název parametru**

  Nastaví název parametru, který přidáváte pro vlastnost, pokud vlastnost má parametry. Jakmile vyberete **přidat**, zobrazí se název **parametru**v seznamu Parametr .

- **Seznam parametrů**

  Zobrazí seznam atributů, které mají být přidány do vlastnosti. Každá položka v seznamu se skládá z názvu parametru, typu parametru a atributů. Chcete-li aktualizovat **seznam,** použijte použít možnost Přidat a **odebrat.**

- **Přidat**

  Přidá zadaný parametr v **poli Název parametru** a **typ parametru** do **seznamu Parametr**. Vyberte **Přidat,** chcete-li přidat parametr do seznamu.

- **Odebrat**

  Odebere parametr vybraný v **seznamu Parametry**.

- **Výchozí vlastnost**

  Pouze rozhraní dispinterface knihovny MFC. Nastaví tuto vlastnost jako výchozí pro rozhraní. Rozhraní může mít pouze jednu výchozí vlastnost; jakmile zadáte výchozí vlastnost, pro všechny ostatní vlastnosti, které přidáte do rozhraní, toto pole není k dispozici.

## <a name="idl-attributes-add-property-wizard"></a>Atributy IDL, Průvodce přidáním vlastností

Na této stránce Průvodce přidáním vlastností můžete určit nastavení jazyka definice rozhraní (IDL) pro vlastnost.

- `id`

  Nastaví číselné ID, které identifikuje vlastnost. Tato možnost není k dispozici pro vlastnosti vlastních rozhraní. Viz [id](/windows/win32/Midl/id) v *odkazu MIDL*.

- `helpcontext`

  Určuje ID kontextu, které umožňuje uživateli zobrazit informace o této vlastnosti v souboru nápovědy. Viz [helpcontext](/windows/win32/Midl/helpcontext) v *odkazu MIDL*.

- `helpstring`

  Určuje řetězec znaků, který se používá k popisu prvku, na který se vztahuje. Ve výchozím nastavení je `property` &nbsp;nastavena na *název vlastnosti&nbsp;*. Viz [helpstring](/windows/win32/Midl/helpstring) v *odkazu MIDL*.

### <a name="other-options"></a>Další možnosti

Ne všechny možnosti jsou k dispozici pro všechny typy vlastností.

|Možnost|Popis|
|------------|-----------------|
|`bindable`|Označuje, že vlastnost podporuje datové vazby. Viz [vazba v](/windows/win32/Midl/bindable) *odkazu MIDL*. Pro burzovní implementaci vlastnosti je tato možnost nastavena ve výchozím nastavení a je neměnná.|
|`defaultbind`|Označuje, že tato jediná vlastnost s vazbou nejlépe představuje objekt. Viz [defaultbind](/windows/win32/Midl/defaultbind) v *odkazu MIDL*.|
|`displaybind`|Označuje, že tato vlastnost by měla být zobrazena uživateli jako vyvažovatelné. Viz [displaybind](/windows/win32/Midl/displaybind) v *odkazu MIDL*.|
|`immediatebind`|Označuje, že databáze bude okamžitě upozorněna na všechny změny této vlastnosti objektu vázaného na data. Viz [immediatebind](/windows/win32/Midl/immediatebind) v *odkazu MIDL*.|
|`defaultcollelem`|Označuje, že vlastnost je přistupující funkce pro prvek výchozí kolekce. Viz [defaultcollelem](/windows/win32/Midl/defaultcollelem) v *odkazu MIDL*.|
|`nonbrowsable`|Taguje člen rozhraní nebo dispinterface, který by neměl být zobrazen v prohlížeči vlastností. Viz [nonbrowsable](/windows/win32/Midl/nonbrowsable) v *MIDL reference*.|
|`requestedit`|Označuje, že vlastnost `OnRequestEdit` podporuje oznámení. Viz [requestedit](/windows/win32/Midl/requestedit) v *odkazu MIDL*. Pro burzovní implementaci vlastnosti je tato možnost nastavena ve výchozím nastavení a je neměnná.|
|`source`|Označuje, že člen vlastnosti je zdrojem událostí. Viz [zdroj](/windows/win32/Midl/source) v *odkazu MIDL*.|
|`hidden`|Označuje, že vlastnost existuje, ale neměla by být zobrazena v prohlížeči orientovaném na uživatele. Viz [skryté](/windows/win32/Midl/hidden) v *odkazu MIDL*.|
|`restricted`|Určuje, že vlastnost nelze volat libovolně. Viz [omezení](/windows/win32/Midl/restricted) v *odkazu MIDL*.|
|`local`|Určuje kompilátoru MIDL, že vlastnost není vzdálená. Viz [místní](/windows/win32/Midl/local) v *odkazu MIDL*.|

## <a name="stock-properties"></a>Skladové nemovitosti

Pokud přidáváte vlastnost do rozhraní dispinterface knihovny MFC pomocí [průvodce přidáním vlastností](#idl-attributes-add-property-wizard), můžete zvolit vlastnost stock ze seznamu **Název vlastnosti** na stránce [Názvy](../ide/names-add-property-wizard.md) průvodce. Tyto vlastnosti jsou následující:

|Název vlastnosti|Popis|
|-------------------|-----------------|
|`Appearance`|Vrátí nebo nastaví hodnotu, která určuje vzhled ovládacího prvku. Vlastnost ovládacího `Appearance` prvku může zahrnovat nebo vynechat trojrozměrné efekty zobrazení. Tato vlastnost je okolní čtení a zápis vlastnost.|
|`BackColor`|Vrátí nebo nastaví vlastnost `BackColor` okolí ovládacího prvku buď na barvu palety (RGB), nebo na předdefinovanou systémovou barvu. Ve výchozím nastavení jeho hodnota odpovídá barvě popředí kontejneru ovládacího prvku. Tato vlastnost je okolní čtení a zápis vlastnost.|
|`BorderStyle`|Vrátí nebo nastaví styl ohraničení ovládacího prvku. Tato vlastnost je vlastnost pro čtení a zápis.|
|`Caption`|Vrátí nebo nastaví `Caption` vlastnost ovládacího prvku. Titulek je název okna. `Caption`nemá žádný typ implementace **členské proměnné.**|
|`Enabled`|Vrátí nebo nastaví `Enabled` vlastnost ovládacího prvku. Povolený ovládací prvek může reagovat na události generované uživatelem.|
|`Font`|Vrátí nebo nastaví okolní písmo ovládacího prvku. Null, pokud ovládací prvek nemá žádné písmo.|
|`ForeColor`|Vrátí nebo nastaví okolní `ForeColor` vlastnost ovládacího prvku.|
|`hWnd`|Vrátí nebo nastaví `hWnd` vlastnost ovládacího prvku. `hWnd`nemá žádný typ implementace **členské proměnné.**|
|`ReadyState`|Vrátí nebo nastaví `ReadyState` vlastnost ovládacího prvku. Ovládací prvek může být uninitialized, inicializované, načítání, interaktivní nebo úplné. Další informace naleznete v tématu [READYSTATE](/previous-versions/aa768362\(v=vs.85\)) v *internetové sdk .*|
|`Text`|Vrátí nebo nastaví text obsažený v ovládacím prvku. `Text`nemá žádný typ implementace **členské proměnné.**|
