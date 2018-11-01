---
title: Názvy, Průvodce přidáním vlastnosti
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.prop.overview
ms.assetid: 0453b7ea-89cb-41a1-80a2-d45f61589c0a
ms.openlocfilehash: 1cb37b2e8f3efd9ff9789a315e6bf32add730708
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636914"
---
# <a name="names-add-property-wizard"></a>Názvy, Průvodce přidáním vlastnosti

Tohoto průvodce použijte k přidání vlastnosti do rozhraní.

- **Typ vlastnosti**

   Nastaví typ vlastnosti, kterou chcete přidat. Pro odesílající rozhraní knihovny MFC zadejte vlastní typ nebo vybrat z předdefinovaného seznamu. Pokud zadáte základní implementaci vlastnosti, **typ vlastnosti** nastavený základní typ a není možné měnit.

- **Název vlastnosti**

   Nastaví název vlastnosti. Pro odesílající rozhraní knihovny MFC související s ovládacími prvky ActiveX můžete zadat vlastní název nebo název uložených vlastností můžete vybrat z předdefinovaného seznamu. Pokud zadáte název vlastní vlastnosti **akcie** typ implementace není k dispozici. Zobrazit [uložené vlastnosti](../ide/stock-properties.md) popis vlastnosti v seznamu.

   |Typ rozhraní|Popis|
   |--------------------|-----------------|
   |Duální rozhraní ATL, vlastní rozhraní a vlastní místní rozhraní|Zadejte název vlastnosti.|
   |Dispinterface knihovny MFC, dispinterface ovládací prvek ActiveX knihovny MFC|Zadejte název vlastnosti nebo vyberte ze seznamu uložených vlastností. Pokud vyberete vlastnost ze seznamu, se zobrazí odpovídající hodnotu v **typ vlastnosti** pole. Tento typ můžete měnit v závislosti na výběru v rámci **typ implementace**.|

- **Návratový typ**

   Knihovny ATL pouze rozhraní. Nastaví návratový typ pro vlastnost. Pro duální rozhraní `HRESULT` je vždy návratový typ a toto pole je k dispozici. Pro vlastní rozhraní můžete vybrat typ vrácené hodnoty ze seznamu. `HRESULT` je přesto vám doporučujeme, protože poskytuje standardní způsob, jak vrátit chyby.

- **Název proměnné**

   Pouze odesílající rozhraní knihovny MFC. K dispozici pouze v případě, že zadáte **členskou proměnnou** pod **typ implementace**. Nastaví název členské proměnné, ke kterému je přidružena vlastnost. Ve výchozím nastavení, název proměnné je nastaven na m_*PropertyName*. Můžete upravit tento název.

- **Funkce oznámení**

   Pouze odesílající rozhraní knihovny MFC. K dispozici pouze v případě, že zadáte **členskou proměnnou** pod **typ implementace**. Nastaví název if volané funkce oznámení změn vlastností. Ve výchozím nastavení, název funkce oznámení nastavena na*PropertyName*změněné. Můžete upravit tento název.

- **Funkce Get**

   Pro odesílající rozhraní knihovny MFC. K dispozici pouze v případě, že zadáte **metody Get/Set** pod **typ implementace**. Nastaví název funkce Get pro vlastnost. Ve výchozím nastavení, název funkce Get nastavena na hodnotu Get*PropertyName*. Můžete upravit tento název. Pokud odstraníte název funkce [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) je vložen do mapy odbavení rozhraní. Získat*PropertyName* funkce určuje, že vlastnost jako čitelný.

- **Funkci set**

   Pouze odesílající rozhraní knihovny MFC. K dispozici pouze v případě, že zadáte **metody Get/Set** pod **typ implementace**. Nastaví název funkce pro nastavení vlastnosti. Ve výchozím nastavení, je název funkce Set nastavený na sadu*PropertyName*. Můžete upravit tento název. Pokud odstraníte název funkce [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) je vložen do mapy odbavení rozhraní. Sada*PropertyName* funkce určuje zapisovatelnou vlastnost.

- **Typ implementace**

   Pouze odesílající rozhraní knihovny MFC. Určuje, jak implementovat vlastnost, kterou chcete přidat.

   |Typ implementace|Popis|
   |-------------------------|-----------------|
   |**Stock**|Určuje základní implementaci pro vlastnost vybrané v **název vlastnosti**. Výchozí nastavení Zobrazit [uložené vlastnosti](../ide/stock-properties.md) Další informace.<br /><br /> Pokud zadáte **akcie**, pak **typ vlastnosti**, **typ parametru**, a **název parametru** jsou neaktivní.|
   |**Členské proměnné**|Určuje, že vlastnost je přidán jako členské proměnné. Jako členské proměnné můžete přidat vlastní vlastnosti nebo většinu uložených vlastností. Nelze zadat **členskou proměnnou** pro **titulek**, **hWnd**, a **Text** vlastnosti.<br /><br /> Poskytuje výchozí názvy v rámci **název proměnné** a **funkce oznámení**. Můžete upravit tento název.|
   |**Metody Get/Set**|Určuje vlastnost se přidá jako Get*PropertyName* a nastavte*PropertyName* funkce ve výchozím nastavení. Tyto názvy se zobrazí pod **funkce Get** a **funkce Set**.<br /><br /> Můžete změnit výchozí **typ vlastnosti**, která předá hodnotu pro funkci Get. Můžete zadat parametry pro **získat** a `Set` funkce.|

- **Funkce Get**

   Pro knihovny ATL rozhraní. Nastaví vlastnost jako čitelný; To znamená, že vytvoří **získat** metodu pro načtení této vlastnosti z objektu. Musíte vybrat **získat**, `Put`, nebo obojí.

- **PUT – funkce**

   Knihovny ATL pouze rozhraní. Nastaví vlastnost jako zapisovatelný; To znamená, že vytvoří `Put` metodu pro nastavení, nebo "umístění" tuto vlastnost v objektu. Musíte vybrat **získat**, `Put`, nebo obojí. Pokud vyberete tuto možnost, můžete z následující dva způsoby, jak implementovat metodu:

   |Možnost|Popis|
   |------------|-----------------|
   |**PropPut**|[PropPut](../windows/propput.md) funkce vrátí kopii objektu. Toto je výchozí a nejběžnější způsob umožnit zápis vlastnosti.|
   |**PropPutRef**|[PropPutRef](../windows/propputref.md) funkce vrátí odkaz na objekt, spíše než vrácení kopie samotného objektu. Zvažte použití této možnosti pro objekty, jako je například velké struktur nebo pole, které mohou mít režijní náklady na inicializaci.|

- **Atributy parametru**

   Knihovny ATL pouze rozhraní. Nastaví, zda určený parametr **název parametru** je **v**, **si**, oba, nebo žádný.

   |Možnost|Popis|
   |------------|-----------------|
   |**in**|Označuje, že parametr je předán z volající procedury do volané procedury.|
   |**out**|Označuje, že parametr ukazatel se vrátí z volané procedury do volající procedury (ze serveru do klienta).|

- **Typ parametru**

   Nastaví datový typ parametru. Vyberte typ ze seznamu.

- **Název parametru**

   Nastaví název parametru, který chcete přidat vlastnosti, pokud má vlastnost parametry. Po kliknutí na **přidat**, zobrazí se název parametru v **seznam parametrů**.

- **Seznam parametrů**

   Zobrazí seznam atributů, které mají být přidána do vlastnosti. Každá položka v seznamu se skládá z názvu parametru, typ parametru a atributy. Použití **přidat** a **odebrat** k aktualizaci seznamu.

- **Add**

   Přidá parametr, který jste zadali v **název parametru** a **typ parametru** k **seznam parametrů**. Musíte kliknout na **přidat** přidání parametru do seznamu.

- **odebrat**

   Odstraní parametr vyberete v **seznam parametrů**.

- **Výchozí vlastnost**

   Pouze odesílajícího rozhraní knihovny MFC. Tato vlastnost nastaví jako výchozí rozhraní. Rozhraní může mít pouze jeden výchozí vlastnosti; Po zadání výchozí vlastnost pro další vlastnosti, které přidáte do rozhraní, toto pole je k dispozici.

## <a name="see-also"></a>Viz také

[Přidání vlastnosti](../ide/adding-a-property-visual-cpp.md)<br>
[IDL – atributy, Průvodce přidáním vlastnosti](../ide/idl-attributes-add-property-wizard.md)<br>
[Implementace rozhraní](../ide/implementing-an-interface-visual-cpp.md)