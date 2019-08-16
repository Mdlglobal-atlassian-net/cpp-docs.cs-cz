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
ms.openlocfilehash: 5c472b74fee690c0cf33f78eca9e2e8462930eb8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509527"
---
# <a name="add-a-property"></a>Přidání vlastnosti

[Průvodce přidáním vlastnosti](#names-add-property-wizard) můžete použít k přidání metody do rozhraní v projektu.

**Přidání vlastnosti do objektu:**

1. V [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code)klikněte pravým tlačítkem myši na název rozhraní, ke kterému chcete přidat vlastnost.

   > [!NOTE]
   > Můžete také přidat vlastnosti do odesílajícího rozhraní, které, pokud není projekt atributem, jsou vnořeny do uzlu knihovny.

1. V místní nabídce klikněte na položku **Přidat**a poté zvolte možnost **Přidat vlastnost**.

1. V [Průvodci přidáním vlastnosti](#names-add-property-wizard)zadejte informace pro vytvoření vlastnosti.

1. Určete libovolné nastavení IDL (Interface Definition Language) pro vlastnost na stránce s [atributy IDL](#idl-attributes-add-property-wizard) průvodce.

1. Kliknutím na tlačítko **Dokončit** přidejte vlastnost.

Metody `Get` a`Put` vlastnosti jsou zobrazeny jako dvě ikony v zobrazení tříd v rámci rozhraní, ve kterém je definována. Můžete dvakrát kliknout na ikonu pro zobrazení deklarace vlastnosti v souboru. idl.

- V `Get` případě rozhraní ATL jsou funkce `Put` a přidány do souboru. cpp a odkazy na tyto funkce jsou přidány do souboru. h.

- Pro odesílající rozhraní knihovny MFC, pokud vyberete **členskou proměnnou** jako typ implementace, je metoda a proměnná přidána do třídy, která ji implementuje. Vyberete-li jako typ implementace **metody get/set** , jsou do třídy, která ji implementuje, přidány dvě metody.

## <a name="in-this-section"></a>V tomto oddílu

- [Názvy, Průvodce přidáním vlastnosti](#names-add-property-wizard)
- [IDL – atributy, Průvodce přidáním vlastnosti](#idl-attributes-add-property-wizard)
- [Uložené vlastnosti](#stock-properties)

## <a name="names-add-property-wizard"></a>Názvy, Průvodce přidáním vlastnosti

Pomocí tohoto průvodce můžete přidat vlastnost do rozhraní.

- **Typ vlastnosti**

  Nastaví typ vlastnosti, kterou přidáváte. Pro odesílající rozhraní knihovny MFC zadejte vlastní typ nebo vyberte z předdefinovaného seznamu. Pokud zadáte základní implementaci vlastnosti, **typ vlastnosti** je nastaven na burzovní typ a není k dispozici pro změnu.

- **Název vlastnosti**

  Nastaví název vlastnosti. Pro odesílající rozhraní knihovny MFC přidružené k ovládacím prvkům ActiveX můžete dodat vlastní název, nebo můžete vybrat název vlastnosti z předdefinovaného seznamu. Pokud zadáte název vlastní vlastnosti, není dostupný typ základní implementace. Popis vlastností v seznamu naleznete v tématu [uložené vlastnosti](#stock-properties) .

  |Typ rozhraní|Popis|
  |--------------------|-----------------|
  |Duální rozhraní ATL, vlastní rozhraní a místní vlastní rozhraní|Zadejte název vlastnosti.|
  |Odesílající rozhraní MFC, odesílající rozhraní ovládacího prvku ActiveX knihovny MFC|Zadejte název vlastnosti nebo vyberte ze seznamu vlastnost akcie. Pokud vyberete vlastnost ze seznamu, zobrazí se příslušná hodnota v poli **typ vlastnosti** . Tento typ můžete změnit v závislosti na výběru v části **Typ implementace**.|

- **Návratový typ**

  Pouze rozhraní ATL. Nastaví návratový typ pro vlastnost. Pro duální rozhraní `HRESULT` je vždy návratový typ a toto pole je nedostupné. Pro vlastní rozhraní můžete vybrat návratový typ ze seznamu. `HRESULT`stále se doporučuje, protože poskytuje standardní způsob, jak vracet chyby.

- **Název proměnné**

  Pouze odesílající rozhraní knihovny MFC. K dispozici pouze v případě, že zadáte **členskou proměnnou** v části **Typ implementace**. Nastaví název členské proměnné, ke které je vlastnost přidružená. Ve výchozím nastavení je proměnná název nastavena na `m_`hodnotu *PropertyName*. Tento název můžete upravit.

- **Funkce oznámení**

  Pouze odesílající rozhraní knihovny MFC. K dispozici pouze v případě, že zadáte **členskou proměnnou** v části **Typ implementace**. Nastaví název funkce oznámení volané, pokud se změní vlastnost. Ve výchozím nastavení je název funkce oznámení nastaven na `On`hodnotu *PropertyName*`Changed`. Tento název můžete upravit.

- **Funkce Get**

  Pro odesílající rozhraní knihovny MFC. K dispozici pouze v případě, že zadáte **metody get/set** v rámci **typu implementace**. Nastaví název funkce pro získání vlastnosti. Ve výchozím nastavení je název `Get` funkce nastaven na `Get`hodnotu *PropertyName*. Tento název můžete upravit. Pokud název odstraníte, funkce [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) je vložena do mapy odeslání rozhraní. Funkce PropertyName určuje vlastnost jako čitelnou. `Get`

- **Set – funkce**

  Pouze odesílající rozhraní knihovny MFC. K dispozici pouze v případě, že zadáte **metody get/set** v rámci **typu implementace**. Nastaví název funkce pro nastavení vlastnosti. Ve výchozím nastavení je název `Set` funkce nastaven na `Set`hodnotu *PropertyName*. Tento název můžete upravit. Pokud název odstraníte, funkce [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) je vložena do mapy odeslání rozhraní. Funkce PropertyName určuje, zda je vlastnost zapisovatelná. `Set`

- **Typ implementace**

  Pouze odesílající rozhraní knihovny MFC. Určuje, jak implementovat vlastnost, kterou přidáváte.

  |Typ implementace|Popis|
  |-------------------------|-----------------|
  |**Kolejovými**|Určuje uloženou implementaci pro vlastnost vybranou v **názvu vlastnosti**. Výchozí nastavení Další informace najdete v tématu [uložené vlastnosti](#stock-properties).<br /><br /> Pokud zadáte **populaci**, pak **typ vlastnosti**, **typ parametru**a **název parametru** jsou ztlumené.|
  |**Členská proměnná**|Určuje vlastnost, která se přidá jako členská proměnná. Můžete přidat vlastní vlastnosti nebo většinu uložených vlastností jako členské proměnné. Nelze zadat **členskou proměnnou** pro `Caption`vlastnosti, `hWnd`a `Text` .<br /><br /> Poskytuje výchozí názvy v části **název proměnné** a **funkce oznámení**. Tento název můžete upravit.|
  |**Metody get/set**|Určuje, že ve výchozím nastavení `Get`je vlastnost `Set`přidána jako funkce *PropertyName* a *PropertyName* . Tyto názvy se zobrazí v části **načíst funkci** a **funkci set**.<br /><br /> Můžete změnit výchozí **typ vlastnosti**, který předá hodnotu funkce Get. Můžete zadat parametry pro `Get` funkce a. `Set`|

- **Funkce Get**

  Pro rozhraní ATL. Nastaví vlastnost jako čitelnou. To znamená, že vytvoří `Get` metodu pro načtení této vlastnosti z objektu. Vyberte **Get**, **Put**nebo obojí.

- **Put – funkce**

  Pouze rozhraní ATL. Nastaví vlastnost zapisovatelnou; To znamená, že vytvoří `Put` metodu pro nastavení nebo "vložení" této vlastnosti objektu. Vyberte **Get**, **Put**nebo obojí. Pokud vyberete tuto možnost, můžete si vybrat z následujících dvou způsobů implementace metody:

  |Možnost|Popis|
  |------------|-----------------|
  |**PropPut**|Funkce [propput](../windows/propput.md) vrátí kopii objektu. Toto je výchozí a nejběžnější způsob, jak vlastnost nastavit na zapisovatelnou.|
  |**PropPutRef**|Funkce [propputref](../windows/propputref.md) vrací odkaz na objekt namísto vrácení kopie samotného objektu. Zvažte použití této možnosti pro objekty, jako jsou například velké struktury nebo pole, které mohou mít zatížení při inicializaci.|

- **Atributy parametru**

  Pouze rozhraní ATL. Nastaví, zda parametr určený **parametrem Name** má `in`hodnotu `out`,, obojí nebo None.

  |Možnost|Popis|
  |------------|-----------------|
  |`in`|Označuje, že parametr je předán z volající procedury do volané procedury.|
  |`out`|Označuje, že parametr ukazatele je vrácen z volané procedury do volající procedury (ze serveru do klienta).|

- **Typ parametru**

  Nastaví datový typ parametru. Vyberte typ ze seznamu.

- **Název parametru**

  Nastaví název parametru, který přidáváte pro vlastnost, pokud vlastnost obsahuje parametry. Jakmile vyberete možnost **Přidat**, název parametru se zobrazí v **seznamu parametrů**.

- **Seznam parametrů**

  Zobrazí seznam atributů, které mají být přidány do vlastnosti. Každá položka v seznamu se skládá z názvu parametru, typu parametru a atributů. Seznam můžete aktualizovat pomocí **Přidat** a **Odebrat** .

- **Add**

  Přidá do **seznamu parametrů**parametr, který zadáte jako **parametr název** a **typ** parametru. Vyberte **Přidat** a přidejte do seznamu parametr.

- **odebrat**

  Odstraní parametr, který jste vybrali v **seznamu parametrů**.

- **Výchozí vlastnost**

  Pouze odesílající rozhraní MFC. Nastaví tuto vlastnost jako výchozí pro rozhraní. Rozhraní může mít pouze jednu výchozí vlastnost; Po zadání výchozí vlastnosti pro všechny ostatní vlastnosti, které přidáte do rozhraní, není toto pole k dispozici.

## <a name="idl-attributes-add-property-wizard"></a>IDL – atributy, Průvodce přidáním vlastnosti

Tato stránka Průvodce přidáním vlastnosti slouží k určení libovolného nastavení jazyka IDL (Interface Definition Language) pro vlastnost.

- `id`

  Nastaví číselné ID, které identifikuje vlastnost. Tato možnost není k dispozici pro vlastnosti vlastních rozhraní. Viz [ID](/windows/win32/Midl/id) v *odkazu MIDL*.

- `helpcontext`

  Určuje ID kontextu, které uživateli umožňuje zobrazit informace o této vlastnosti v souboru Help. Viz [atribut HelpContext](/windows/win32/Midl/helpcontext) v *odkazu MIDL*.

- `helpstring`

  Určuje řetězec znaků, který se používá k popisu prvku, na který se vztahuje. Ve výchozím nastavení je nastaveno na `property` &nbsp; *název vlastnosti&nbsp;* . Viz [HelpString](/windows/win32/Midl/helpstring) v *odkazu MIDL*.

### <a name="other-options"></a>Další možnosti

Ne všechny možnosti jsou k dispozici pro všechny typy vlastností.

|Možnost|Popis|
|------------|-----------------|
|`bindable`|Označuje, že vlastnost podporuje datové vazby. Viz [vazba](/windows/win32/Midl/bindable) v *odkazu MIDL*. Pro základní implementaci vlastnosti je tato možnost standardně nastavena a nelze ji měnit.|
|`defaultbind`|Označuje, že tato jediná vlastnost s možností vazby nejlépe představuje objekt. Viz [defaultbind](/windows/win32/Midl/defaultbind) v *odkazu MIDL*.|
|`displaybind`|Indikuje, že se tato vlastnost má uživateli zobrazit jako vazba. Viz [displaybind](/windows/win32/Midl/displaybind) v *odkazu MIDL*.|
|`immediatebind`|Označuje, že se bude databáze okamžitě informovat o všech změnách této vlastnosti objektu vázaného na data. Viz [immediatebind](/windows/win32/Midl/immediatebind) v *odkazu MIDL*.|
|`defaultcollelem`|Označuje, že vlastnost je přístupovou funkcí pro prvek výchozí kolekce. Viz [defaultcollelem](/windows/win32/Midl/defaultcollelem) v *odkazu MIDL*.|
|`nonbrowsable`|Označí člena rozhraní nebo odesílajícího objektu, který by se neměl zobrazovat v prohlížeči vlastností. Viz [](/windows/win32/Midl/nonbrowsable) neprocházetelné v *odkazu MIDL*.|
|`requestedit`|Označuje, že vlastnost podporuje `OnRequestEdit` oznámení. Viz [requestedit](/windows/win32/Midl/requestedit) v *odkazu MIDL*. Pro základní implementaci vlastnosti je tato možnost standardně nastavena a nelze ji měnit.|
|`source`|Označuje, že člen vlastnosti je zdrojem událostí. Viz [zdroj](/windows/win32/Midl/source) v *odkazu MIDL*.|
|`hidden`|Označuje, že vlastnost existuje, ale neměla by se zobrazovat v prohlížeči orientovaném na uživatele. Viz [Hidden](/windows/win32/Midl/hidden) v *odkazu MIDL*.|
|`restricted`|Určuje, že vlastnost nemůže být volána libovolně. Viz [omezení](/windows/win32/Midl/restricted) v *odkazu MIDL*.|
|`local`|Určuje kompilátoru MIDL, že vlastnost není vzdálená. Viz [místní](/windows/win32/Midl/local) v *odkazu MIDL*.|

## <a name="stock-properties"></a>Uložené vlastnosti

Pokud přidáváte vlastnost do odesílajícího rozhraní knihovny MFC pomocí [Průvodce přidáním vlastnosti](#idl-attributes-add-property-wizard), můžete vybrat vlastnost akcie ze seznamu **název vlastnosti** na stránce s [názvy](../ide/names-add-property-wizard.md) v průvodci. Tyto vlastnosti jsou následující:

|Název vlastnosti|Popis|
|-------------------|-----------------|
|`Appearance`|Vrátí nebo nastaví hodnotu, která určuje vzhled ovládacího prvku. `Appearance` Vlastnost ovládacího prvku může zahrnovat nebo odpustit trojrozměrné efekty zobrazení. Tato vlastnost je vnější vlastnost pro čtení a zápis.|
|`BackColor`|Vrátí nebo nastaví vlastnost Ambient `BackColor` ovládacího prvku na barvu palety (RGB) nebo předdefinované systémové barvy. Ve výchozím nastavení odpovídá jeho hodnota barva popředí kontejneru ovládacího prvku. Tato vlastnost je vnější vlastnost pro čtení a zápis.|
|`BorderStyle`|Vrátí nebo nastaví styl ohraničení ovládacího prvku. Tato vlastnost je vlastnost pro čtení i zápis.|
|`Caption`|Vrátí nebo nastaví `Caption` vlastnost ovládacího prvku. Popisek je název okna. `Caption`nemá žádný typ implementace **členské proměnné** .|
|`Enabled`|Vrátí nebo nastaví `Enabled` vlastnost ovládacího prvku. Povolený ovládací prvek může reagovat na události generované uživatelem.|
|`Font`|Vrátí nebo nastaví okolí písma ovládacího prvku. Hodnota null, pokud ovládací prvek nemá žádné písmo.|
|`ForeColor`|Vrátí nebo nastaví vlastnost Ambient `ForeColor` ovládacího prvku.|
|`hWnd`|Vrátí nebo nastaví `hWnd` vlastnost ovládacího prvku. `hWnd`nemá žádný typ implementace **členské proměnné** .|
|`ReadyState`|Vrátí nebo nastaví `ReadyState` vlastnost ovládacího prvku. Ovládací prvek může být Neinicializovaný, inicializovaný, načtený, interaktivní nebo úplný. Další informace najdete v tématu [](/previous-versions//aa768362\(v=vs.85\)) Přečtěte si v *sadě Internet SDK*.|
|`Text`|Vrátí nebo nastaví text obsažený v ovládacím prvku. `Text`nemá žádný typ implementace **členské proměnné** .|
