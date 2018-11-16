---
title: Přidat vlastnost
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
ms.openlocfilehash: 06940bb72f9113e0a8148e15418504b35fc95099
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694254"
---
# <a name="add-a-property"></a>Přidat vlastnost

Můžete použít [Průvodce přidáním vlastnosti](#names-add-property-wizard) přidání metody do rozhraní ve vašem projektu.

**Přidání vlastnosti do objektu:**

1. V [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na název rozhraní, ke kterému chcete přidat vlastnost.

   > [!NOTE]
   > Můžete také přidat vlastnosti do odesílacích rozhraních, která pokud je projekt s atributy, jsou vnořené uvnitř uzlu knihovny.

1. V místní nabídce zvolte **přidat**a klikněte na tlačítko **přidat vlastnost**.

1. V [Průvodce přidáním vlastnosti](#names-add-property-wizard), zadejte informace k vytvoření vlastnosti.

1. Zadejte nastavení jakékoli interface definition language (IDL) pro vlastnost [IDL – atributy](#idl-attributes-add-property-wizard) stránky průvodce.

1. Vyberte **Dokončit** přidat vlastnost.

`Get` a `Put` metody, vlastnosti se zobrazí jako dvě ikony v zobrazení tříd v rámci rozhraní, kde je definován. Dvakrát klikněte na ikonu se zobrazí deklarace vlastnosti v souboru IDL.

- Pro rozhraní knihovny ATL `Get` a `Put` funkce jsou přidány do souboru CPP, a odkazy na tyto funkce jsou přidány do souboru hlaviček.

- Pro odesílající rozhraní knihovny MFC, pokud vyberete **členskou proměnnou** jako typ implementace metody a proměnné se přidají do třídy, která jej implementuje. Pokud vyberete **metody Get/Set** jako typ implementace jsou přidány dvě metody do třídy, která jej implementuje.

## <a name="in-this-section"></a>V tomto oddílu

- [Názvy, Průvodce přidáním vlastnosti](#names-add-property-wizard)
- [IDL – atributy, Průvodce přidáním vlastnosti](#idl-attributes-add-property-wizard)
- [Uložené vlastnosti](#stock-properties)

## <a name="names-add-property-wizard"></a>Názvy, Průvodce přidáním vlastnosti

Tohoto průvodce použijte k přidání vlastnosti do rozhraní.

- **Typ vlastnosti**

  Nastaví typ vlastnosti, kterou přidáváte. Pro odesílající rozhraní knihovny MFC zadejte vlastní typ nebo vybrat z předdefinovaného seznamu. Pokud zadáte základní implementaci vlastnosti, **typ vlastnosti** nastavený základní typ a není možné měnit.

- **Název vlastnosti**

  Nastaví název vlastnosti. Pro odesílající rozhraní knihovny MFC související s ovládacími prvky ActiveX můžete zadat vlastní název nebo název uložených vlastností můžete vybrat z předdefinovaného seznamu. Pokud zadáte název vlastní vlastnosti **akcie** typ implementace není k dispozici. Zobrazit [uložené vlastností](#stock-properties) popis vlastnosti v seznamu.

  |Typ rozhraní|Popis|
  |--------------------|-----------------|
  |Duální rozhraní ATL, vlastní rozhraní a vlastní místní rozhraní|Zadejte název vlastnosti.|
  |Dispinterface knihovny MFC, dispinterface ovládací prvek ActiveX knihovny MFC|Zadejte název vlastnosti nebo vyberte ze seznamu uložených vlastností. Pokud vyberete vlastnost ze seznamu, se zobrazí odpovídající hodnotu v **typ vlastnosti** pole. Tento typ můžete měnit v závislosti na výběru v rámci **typ implementace**.|

- **Návratový typ**

  Knihovny ATL pouze rozhraní. Nastaví návratový typ pro vlastnost. Pro duální rozhraní `HRESULT` je vždy návratový typ a toto pole je k dispozici. Pro vlastní rozhraní můžete vybrat typ vrácené hodnoty ze seznamu. `HRESULT` je přesto vám doporučujeme, protože poskytuje standardní způsob, jak vrátit chyby.

- **Název proměnné**

  Pouze odesílající rozhraní knihovny MFC. K dispozici pouze v případě, že zadáte **členskou proměnnou** pod **typ implementace**. Nastaví název členské proměnné, ke kterému je přidružena vlastnost. Ve výchozím nastavení, název proměnné je nastaven `m_` *PropertyName*. Můžete upravit tento název.

- **Funkce oznámení**

  Pouze odesílající rozhraní knihovny MFC. K dispozici pouze v případě, že zadáte **členskou proměnnou** pod **typ implementace**. Nastaví název if volané funkce oznámení změn vlastností. Ve výchozím nastavení, název funkce oznámení nastavený na `On` *PropertyName*`Changed`. Můžete upravit tento název.

- **Funkce Get**

  Pro odesílající rozhraní knihovny MFC. K dispozici pouze v případě, že zadáte **metody Get/Set** pod **typ implementace**. Nastaví název funkce Get pro vlastnost. Ve výchozím nastavení název `Get` funkce je nastavená `Get` *PropertyName*. Můžete upravit tento název. Pokud odstraníte název funkce [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) je vložen do mapy odbavení rozhraní. `Get` *PropertyName* funkce určuje, že vlastnost jako čitelný.

- **Funkci set**

  Pouze odesílající rozhraní knihovny MFC. K dispozici pouze v případě, že zadáte **metody Get/Set** pod **typ implementace**. Nastaví název funkce pro nastavení vlastnosti. Ve výchozím nastavení název `Set` funkce je nastavená `Set` *PropertyName*. Můžete upravit tento název. Pokud odstraníte název funkce [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) je vložen do mapy odbavení rozhraní. `Set` *PropertyName* funkce určuje zapisovatelnou vlastnost.

- **Typ implementace**

  Pouze odesílající rozhraní knihovny MFC. Určuje, jak implementovat vlastnost, kterou přidáváte.

  |Typ implementace|Popis|
  |-------------------------|-----------------|
  |**Stock**|Určuje základní implementaci pro vlastnost vybrané v **název vlastnosti**. Výchozí nastavení Další informace najdete v tématu [uložené vlastností](#stock-properties).<br /><br /> Pokud zadáte **akcie**, pak **typ vlastnosti**, **typ parametru**, a **název parametru** jsou neaktivní.|
  |**Členské proměnné**|Určuje, že vlastnost je přidán jako členské proměnné. Jako členské proměnné můžete přidat vlastní vlastnosti nebo většinu uložených vlastností. Nelze zadat **členskou proměnnou** pro `Caption`, `hWnd`, a `Text` vlastnosti.<br /><br /> Poskytuje výchozí názvy v rámci **název proměnné** a **funkce oznámení**. Můžete upravit tento název.|
  |**Metody Get/Set**|Určuje vlastnost se přidá jako `Get` *PropertyName* a `Set` *PropertyName* funkce ve výchozím nastavení. Tyto názvy se zobrazí pod **funkce Get** a **funkce Set**.<br /><br /> Můžete změnit výchozí **typ vlastnosti**, která předá hodnotu pro funkci Get. Můžete zadat parametry pro `Get` a `Set` funkce.|

- **Funkce Get**

  Pro knihovny ATL rozhraní. Nastaví vlastnost jako čitelný; To znamená, že vytvoří `Get` metodu pro načtení této vlastnosti z objektu. Vyberte **získat**, **umístit**, nebo obojí.

- **PUT – funkce**

  Knihovny ATL pouze rozhraní. Nastaví vlastnost jako zapisovatelný; To znamená, že vytvoří `Put` metodu pro nastavení, nebo "umístění" tuto vlastnost v objektu. Vyberte **získat**, **umístit**, nebo obojí. Pokud vyberete tuto možnost, můžete z následující dva způsoby, jak implementovat metodu:

  |Možnost|Popis|
  |------------|-----------------|
  |**PropPut**|[PropPut](../windows/propput.md) funkce vrátí kopii objektu. Toto je výchozí a nejběžnější způsob umožnit zápis vlastnosti.|
  |**PropPutRef**|[PropPutRef](../windows/propputref.md) funkce vrátí odkaz na objekt, spíše než vrácení kopie samotného objektu. Zvažte použití této možnosti pro objekty, jako je například velké struktur nebo pole, které mohou mít režijní náklady na inicializaci.|

- **Atributy parametru**

  Knihovny ATL pouze rozhraní. Nastaví, zda určený parametr **název parametru** je `in`, `out`, oba, nebo žádný.

  |Možnost|Popis|
  |------------|-----------------|
  |`in`|Označuje, že parametr je předán z volající procedury do volané procedury.|
  |`out`|Označuje, že parametr ukazatel se vrátí z volané procedury do volající procedury (ze serveru do klienta).|

- **Typ parametru**

  Nastaví datový typ parametru. Vyberte typ ze seznamu.

- **Název parametru**

  Nastaví název parametru, který přidáváte pro vlastnost, pokud má vlastnost parametry. Jakmile vyberete **přidat**, zobrazí se název parametru v **seznam parametrů**.

- **Seznam parametrů**

  Zobrazí seznam atributů, které mají být přidána do vlastnosti. Každá položka v seznamu se skládá z názvu parametru, typ parametru a atributy. Použití **přidat** a **odebrat** k aktualizaci seznamu.

- **Add**

  Přidá parametr, který jste zadali v **název parametru** a **typ parametru** k **seznam parametrů**. Vyberte **přidat** přidání parametru do seznamu.

- **odebrat**

  Odstraní parametr vyberete v **seznam parametrů**.

- **Výchozí vlastnost**

  Pouze odesílajícího rozhraní knihovny MFC. Tato vlastnost nastaví jako výchozí rozhraní. Rozhraní může mít pouze jeden výchozí vlastnosti; Po zadání výchozí vlastnost pro další vlastnosti, které přidáte do rozhraní, toto pole je k dispozici.

## <a name="idl-attributes-add-property-wizard"></a>IDL – atributy, Průvodce přidáním vlastnosti

Na této stránce Průvodce přidáním vlastnosti k určení nastavení jakékoli interface definition language (IDL) pro vlastnost.

- `id`

  Nastaví číselné ID identifikující vlastnosti. Tato možnost není dostupná pro vlastnosti vlastního rozhraní. Zobrazit [id](/windows/desktop/Midl/id) v *MIDL odkazu*.

- `helpcontext`

  Určuje ID kontextu, který umožňuje uživateli zobrazit informace o této vlastnosti v souboru nápovědy. Zobrazit [helpcontext](/windows/desktop/Midl/helpcontext) v *MIDL odkazu*.

- `helpstring`

  Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje. Ve výchozím nastavení, je nastavit `property` &nbsp; *vlastnost&nbsp;název*. Zobrazit [helpstring](/windows/desktop/Midl/helpstring) v *MIDL odkazu*.

### <a name="other-options"></a>Další možnosti

Některé možnosti jsou k dispozici pro všechny typy vlastností.

|Možnost|Popis|
|------------|-----------------|
|`bindable`|Označuje, že vlastnost podporuje datové vazby. Zobrazit [umožňujících vazbu](/windows/desktop/Midl/bindable) v *MIDL odkazu*. Pro implementaci vlastnosti tato možnost je ve výchozím nastavení a nejde změnit.|
|`defaultbind`|Označuje, že tato vlastnost podporující vazby, jeden je nejlepší představuje objekt. Zobrazit [defaultbind](/windows/desktop/Midl/defaultbind) v *MIDL odkazu*.|
|`displaybind`|Indikuje, že tato vlastnost se má zobrazovat uživateli jako s možností vazby. Zobrazit [displaybind](/windows/desktop/Midl/displaybind) v *MIDL odkazu*.|
|`immediatebind`|Označuje, že databázi budou okamžitě oznamovat všechny změny této vlastnosti objektu vázané na data. Zobrazit [immediatebind](/windows/desktop/Midl/immediatebind) v *MIDL odkazu*.|
|`defaultcollelem`|Označuje, že je vlastnost přístupovou funkci pro prvek výchozí kolekce. Zobrazit [defaultcollelem](/windows/desktop/Midl/defaultcollelem) v *MIDL odkazu*.|
|`nonbrowsable`|Značky na rozhraní nebo dispinterface člena, který nebude se zobrazovat v prohlížeči vlastností. Zobrazit [nonbrowsable](/windows/desktop/Midl/nonbrowsable) v *MIDL odkazu*.|
|`requestedit`|Označuje, že vlastnost podporuje `OnRequestEdit` oznámení. Zobrazit [requestedit –](/windows/desktop/Midl/requestedit) v *MIDL odkazu*. Pro implementaci vlastnosti tato možnost je ve výchozím nastavení a nejde změnit.|
|`source`|Označuje, že je člen vlastnost Zdroj událostí. Zobrazit [zdroj](/windows/desktop/Midl/source) v *MIDL odkazu*.|
|`hidden`|Označuje, že vlastnost existuje, ale nebude se zobrazovat v prohlížeči uživatele. Zobrazit [skryté](/windows/desktop/Midl/hidden) v *MIDL odkazu*.|
|`restricted`|Určuje, že vlastnost se nedá volat libovolně. Zobrazit [s omezeným přístupem](/windows/desktop/Midl/restricted) v *MIDL odkazu*.|
|`local`|Určuje kompilátor MIDL o tom, že vlastnost není vzdálený. Zobrazit [místní](/windows/desktop/Midl/local) v *MIDL odkazu*.|

## <a name="stock-properties"></a>Uložené vlastnosti

Pokud přidáváte vlastnost dispinterface MFC pomocí [Průvodce přidáním vlastnosti](#idl-attributes-add-property-wizard), můžete použít uložených vlastností z **název vlastnosti** v seznamu [názvy](../ide/names-add-property-wizard.md) stránku Průvodce. Tyto vlastnosti jsou následující:

|Název vlastnosti|Popis|
|-------------------|-----------------|
|`Appearance`|Vrací nebo nastavuje hodnotu, která určuje vzhled ovládacího prvku. Ovládací prvek `Appearance` vlastnosti můžete zahrnout nebo vynechejte efekty trojrozměrného zobrazení. Tato vlastnost je vlastnost okolí čtení a zápisu.|
|`BackColor`|Vrací nebo nastavuje okolí ovládacího prvku `BackColor` vlastnost barvu z palety (RGB) nebo předdefinovaných systémových barev. Ve výchozím nastavení jeho hodnota odpovídá barvu popředí ovládacího prvku kontejneru. Tato vlastnost je vlastnost okolí čtení a zápisu.|
|`BorderStyle`|Vrátí nebo nastaví styl ohraničení ovládacího prvku. Tato vlastnost je vlastnost pro čtení a zápisu.|
|`Caption`|Vrátí nebo nastaví ovládací prvek `Caption` vlastnost. Popisek je záhlaví okna. `Caption` nemá žádné **členskou proměnnou** typ implementace.|
|`Enabled`|Vrátí nebo nastaví ovládací prvek `Enabled` vlastnost. Ovládací prvek povolený může reagovat na události generované uživatelem.|
|`Font`|Vrátí nebo nastaví písmo ovládacího prvku. Hodnota Null, pokud ovládací prvek nemá žádné písmo.|
|`ForeColor`|Vrací nebo nastavuje okolí ovládacího prvku `ForeColor` vlastnost.|
|`hWnd`|Vrátí nebo nastaví ovládací prvek `hWnd` vlastnost. `hWnd` nemá žádné **členskou proměnnou** typ implementace.|
|`ReadyState`|Vrátí nebo nastaví ovládací prvek `ReadyState` vlastnost. Ovládací prvek může být neinicializované, inicializován, načítání, interaktivní nebo dokončení. Další informace najdete v tématu [READYSTATE](https://msdn.microsoft.com/library/aa768362.aspx) v *Internet SDK*.|
|`Text`|Vrátí nebo nastaví text obsažen v ovládacím prvku. `Text` nemá žádné **členskou proměnnou** typ implementace.|
