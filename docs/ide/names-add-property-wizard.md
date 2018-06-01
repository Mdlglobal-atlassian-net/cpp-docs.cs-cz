---
title: Názvy, Průvodce přidáním vlastnosti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.prop.overview
dev_langs:
- C++
ms.assetid: 0453b7ea-89cb-41a1-80a2-d45f61589c0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17c3fd5cfc86f76fcdc1c301bd92bb1fdfac3b9c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33339563"
---
# <a name="names-add-property-wizard"></a>Názvy, Průvodce přidáním vlastnosti
Tento průvodce slouží k přidání vlastnosti do rozhraní.  
  
 **Typ vlastnosti**  
 Nastaví typ vlastnosti, který chcete přidat. Pro odesílající rozhraní MFC zadat vlastní typ nebo vyberte ze seznamu předdefinovaných. Pokud zadáte uloženou implementaci vlastnosti, **typ vlastnosti** nastavena na uložený typ a není možné měnit.  
  
 **Název vlastnosti**  
 Nastaví název vlastnosti. Pro odesílající rozhraní MFC související s ovládacími prvky ActiveX můžete zadat vlastní název nebo název uložených vlastností můžete vybrat z předdefinovaného seznamu. Pokud jste zadali vlastní název vlastnosti **Stock** implementace typ není k dispozici. V tématu [uložené vlastnosti](../ide/stock-properties.md) popis v seznamu vlastností.  
  
|Typ rozhraní|Popis|  
|--------------------|-----------------|  
|Duální rozhraní ATL, vlastní rozhraní a vlastní místní rozhraní|Zadejte název vlastnosti.|  
|MFC dispinterface, rozhraní ovládacího prvku ActiveX knihovny MFC|Zadejte název vlastnosti, nebo vyberte uložených vlastností ze seznamu. Pokud vyberete vlastnost ze seznamu, se zobrazí na odpovídající hodnotu v **typ vlastnosti** pole. Tento typ, můžete změnit v závislosti na vašem výběru v položce **typem implementace**.|  
  
 **Návratový typ**  
 Pouze rozhraní ATL Nastaví návratový typ vlastnosti. Pro duální rozhraní `HRESULT` je vždy návratový typ a toto pole je k dispozici. Pro vlastní rozhraní můžete vybrat návratový typ ze seznamu. `HRESULT` se stále doporučuje, protože poskytuje standardní způsob, jak vracet chyby.  
  
 **Název proměnné**  
 Pouze odesílající rozhraní MFC. K dispozici pouze v případě, že zadáte **členské proměnné** pod **typem implementace**. Nastaví název členské proměnné, ke kterému je přiřazeno vlastnost. Ve výchozím nastavení je název proměnné nastaven na m_*PropertyName*. Můžete upravit tento název.  
  
 **Funkce oznámení**  
 Pouze odesílající rozhraní MFC. K dispozici pouze v případě, že zadáte **členské proměnné** pod **typem implementace**. Nastaví název Pokud volané funkce oznámení změny vlastností. Ve výchozím nastavení, je funkce oznámení je nastavit název na*PropertyName*změněno. Můžete upravit tento název.  
  
 **Funkce Get**  
 Pro odesílající rozhraní MFC. K dispozici pouze v případě, že zadáte **metody Get/Set** pod **typem implementace**. Nastaví název funkce Get pro vlastnost. Ve výchozím nastavení, je název funkce Get hodnotu Get*PropertyName*. Můžete upravit tento název. Pokud odstraníte název funkce [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) vložena do mapy odesílání rozhraní. Zjištění*PropertyName* funkce určuje, že vlastnost jako čitelný.  
  
 **Set – funkce**  
 Pouze odesílající rozhraní MFC. K dispozici pouze v případě, že zadáte **metody Get/Set** pod **typem implementace**. Nastaví název funkce Set pro vlastnost. Ve výchozím nastavení, je název funkce Set nastaven k sadě*PropertyName*. Můžete upravit tento název. Pokud odstraníte název funkce [SetNotSupported –](../mfc/reference/colecontrol-class.md#setnotsupported) vložena do mapy odesílání rozhraní. Sada*PropertyName* funkce určuje, že je vlastnost s možností zápisu.  
  
 **Typ implementace**  
 Pouze odesílající rozhraní MFC. Určuje, jak implementovat vlastnost, kterou chcete přidat.  
  
|Typ implementace|Popis|  
|-------------------------|-----------------|  
|**Stock**|Určuje uloženou implementaci pro vlastnost vybranou v **název vlastnosti**. Výchozí nastavení V tématu [uložené vlastnosti](../ide/stock-properties.md) Další informace.<br /><br /> Pokud zadáte **Stock**, pak **typ vlastnosti**, **typ parametru**, a **název parametru** jsou neaktivní.|  
|**Členské proměnné**|Určuje, že vlastnost byla přidána jako členské proměnné. Jako členské proměnné můžete přidat vlastní vlastnosti nebo většinu uložených vlastností. Nelze zadat **členské proměnné** pro **popisek**, **hWnd**, a **Text** vlastnosti.<br /><br /> Poskytuje výchozí názvy v rámci **název proměnné** a **funkce oznámení**. Můžete upravit tento název.|  
|**Metody Get/Set**|Určuje vlastnost přidán jako Get*PropertyName* a nastavte*PropertyName* funkce ve výchozím nastavení. Tyto názvy se zobrazí pod **získat funkce** a **nastavit funkce**.<br /><br /> Můžete změnit výchozí **typ vlastnosti**, která předá hodnotu funkce Get. Můžete zadat parametry pro **získat** a `Set` funkce.|  
  
 **Funkce Get**  
 Pro knihovny ATL rozhraní. Nastaví vlastnost jako čitelný; To znamená, že vytvoří **získat** metody pro získání této vlastnosti z objektu. Je nutné vybrat **získat**, `Put`, nebo obojí.  
  
 **PUT – funkce**  
 Pouze rozhraní ATL Nastaví vlastnost jako zapisovatelnou; To znamená, že vytvoří `Put` metodu pro nastavení, nebo "vložení" Tato vlastnost objektu. Je nutné vybrat **získat**, `Put`, nebo obojí. Pokud vyberete tuto možnost, můžete z následujících dvou způsobů implementovat metodu:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Propput –**|[Propput –](../windows/propput.md) funkce vrátí kopii objektu. Toto je výchozí a nejběžnější způsob vytvoření zapisovatelné vlastnosti.|  
|**Propputref –**|[PropPutRef](../windows/propputref.md) funkce vrátí odkaz na objekt, namísto vrácení kopii samotného objektu. Zvažte použití této možnosti pro objekty, jako je například velké struktury nebo pole, které mohou mít režijní náklady na inicializace.|  
  
 **Atributy parametru**  
 Pouze rozhraní ATL Nastaví, zda zadaný parametr podle **název parametru** je **v**, **out**, oba, nebo žádný.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**in**|Označuje, že parametr se předává z volání procedury vyvolání procedury.|  
|**out**|Označuje, že je parametr ukazatele vrácená z volané procedury volání procedury (ze serveru do klienta).|  
  
 **Typ parametru**  
 Nastaví datový typ parametru. Vyberte typ ze seznamu.  
  
 **Název parametru**  
 Nastaví název parametru, který chcete přidat pro vlastnost, pokud vlastnost obsahuje parametry. Po kliknutí na tlačítko **přidat**, název parametru se zobrazí v **seznam parametrů**.  
  
 **Seznam parametrů**  
 Zobrazí se seznam atributů, které mají být přidána do vlastnosti. Každá položka v seznamu se skládá z názvu parametru, typ parametru a atributy. Použití **přidat** a **odebrat** k aktualizaci seznamu.  
  
 **Přidat**  
 Přidá parametr zadáte v **název parametru** a **typ parametru** k **seznam parametrů**. Musíte kliknout na **přidat** přidání parametru do seznamu.  
  
 **Odebrat**  
 Odebere parametr vyberete v **seznam parametrů**.  
  
 **Výchozí vlastnosti**  
 Pouze odesílající rozhraní MFC. Tato vlastnost nastaví jako výchozí pro rozhraní. Rozhraní může mít pouze jeden výchozí vlastnost; Jakmile zadáte výchozí vlastnost pro všechny vlastnosti, které přidáte do rozhraní, toto pole je k dispozici.  
  
## <a name="see-also"></a>Viz také  
 [Přidání vlastnosti](../ide/adding-a-property-visual-cpp.md)   
 [IDL – atributy, Průvodce přidáním vlastnosti](../ide/idl-attributes-add-property-wizard.md)   
 [Implementace rozhraní](../ide/implementing-an-interface-visual-cpp.md)