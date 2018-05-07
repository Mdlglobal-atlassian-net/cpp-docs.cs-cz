---
title: Průvodce přidáním metody | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.method.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Method Wizard [C++]
- methods [C++], adding using wizards
ms.assetid: b9a71b0e-9ecf-40fa-9f86-4200cb23d671
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cc2ebd18640f0ab778cb45252691e63206861d53
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="add-method-wizard"></a>Průvodce přidáním metody
Pomocí tohoto Průvodce přidání metody do rozhraní. V závislosti na typu projektu nebo na kterou přidáváte metodu typ rozhraní Průvodce zobrazí různé možnosti.  
  
## <a name="names"></a>Názvy  
 **Návratový typ**  
 Datový typ vrácený metodou. `HRESULT` doporučuje se pro všechny typy rozhraní, protože poskytuje standardní způsob, jak vracet chyby.  
  
|Typ rozhraní|Popis|  
|--------------------|-----------------|  
|Duální rozhraní|`HRESULT`. Neměnný.|  
|Vlastní rozhraní|`HRESULT`. Neměnný.|  
|Vlastní místní rozhraní|Zadejte vlastní návratový typ, nebo vyberte ze seznamu.|  
|Dispinterface|Zadejte vlastní návratový typ, nebo vyberte ze seznamu.|  
|Rozhraní ovládacího prvku ActiveX knihovny MFC|Pokud budete implementovat uložené metody, návratový typ je nastaven na odpovídající hodnotu a neměnný. Pokud vyberete metodu z **název metody** seznamu a klikněte na tlačítko **vlastní** pod **vyberte typ metody**, vyberte návratový typ ze seznamu.|  
  
 **Název metody**  
 Nastaví název metody.  
  
|Typ rozhraní|Popis|  
|--------------------|-----------------|  
|Duální rozhraní ATL, vlastní rozhraní a vlastní místní rozhraní|Zadejte název vlastní metody.|  
|Odesílající rozhraní MFC|Zadejte název vlastní metody nebo vyberte navrhovaný název ze seznamu. Pokud vyberete název ze seznamu, se zobrazí na odpovídající hodnotu v **návratový typ** pole a neměnný.|  
|Rozhraní ovládacího prvku ActiveX knihovny MFC|Zadejte vlastní nebo vyberte některou z uložených metod [DoClick –](../mfc/reference/colecontrol-class.md#doclick) a [aktualizovat](../mfc/reference/colecontrol-class.md#refresh). V tématu [MFC – ovládací prvky ActiveX: Přidání uložených metod](../mfc/mfc-activex-controls-adding-stock-methods.md) Další informace.|  
  
 **Typ metody**  
 K dispozici pouze pro ovládací prvky MFC ActiveX. Pokud zadáte název metody v **název metody** pole, místo ze seznamu vyberte metodu, toto pole je k dispozici.  
  
 Pokud vyberete jednu z metod v **název metody** vyberte uloženou nebo vlastní implementaci.  
  
|Typ metody|Popis|  
|-----------------|-----------------|  
|**Stock**|Výchozí nastavení Vloží uloženou implementaci metody vyberete v **název metody** seznamu. **Návratový typ** neměnný, pokud vyberete **Stock**.|  
|**Vlastní**|Vloží prázdnou implementaci metody vybrané v **název metody** seznamu. Pro vlastní metoda typy, můžete zadat vlastní návratový typ, nebo můžete vybrat jednu z **návratový typ** seznamu.|  
  
 **Interní název**  
 K dispozici pouze pro vlastní metody přidat do odesílajícím rozhraním knihovny MFC. Nastaví název používaný v mapě odeslání, soubor hlavičky () a soubor implementace (sada). Ve výchozím nastavení, tento název je stejný jako **název metody**. Pokud pracujete s odesílajícím rozhraním knihovny MFC nebo pokud přidáváte vlastní metoda do rozhraní ovládacího prvku ActiveX knihovny MFC, můžete změnit název metody.  
  
|Typ rozhraní|Popis|  
|--------------------|-----------------|  
|Duální rozhraní ATL, vlastní rozhraní a vlastní místní rozhraní|Není k dispozici|  
|Odesílající rozhraní MFC|Ve výchozím nastavení má název metody. Můžete upravit interní název.|  
|Rozhraní ovládacího prvku ActiveX knihovny MFC|Můžete nastavit jenom interní název vlastní metody. Uložené metody nepoužívají interní název.|  
  
 **Atributy parametru**  
 Nastaví další atributy pro zadané v parametru **název parametru**.  
  
|Atribut parametru|Popis|Povolené kombinace|  
|-------------------------|-----------------|--------------------------|  
|**V**|Označuje, že parametr se předává z volání procedury vyvolání procedury.|**v** pouze<br /><br /> **v** a **out**|  
|**na více systémů**|Označuje, že je parametr ukazatele vrácená z volané procedury volání procedury (ze serveru do klienta).|**out** pouze<br /><br /> **v** a **out**<br /><br /> **out** a **retval –**|  
|**retval –**|Označuje, že parametr obdrží hodnotu vrácenou člena.|**retval –** a na víc systémů|  
  
 **Typ parametru**  
 Nastaví datový typ parametru. Vyberte typ ze seznamu.  
  
 **Název parametru**  
 Nastaví název parametru pro předány metodě. Po zadání názvu, musíte kliknout na **přidat** ho přidejte do seznamu parametrů, které budou předány metodě. Pokud nezadáte název parametru, průvodce ignoruje všechny atributy parametru (pouze ATL) nebo **typ parametru** výběry.  
  
 Po kliknutí na tlačítko **přidat**, název parametru se zobrazí v **seznam parametrů**.  
  
 **Poznámka:** Pokud zadáte název parametru a pak klikněte na tlačítko **Dokončit** před kliknutím na **přidat**, není parametr přidán do metody. Je nutné vyhledat metodu a vložit parametr ručně.  
  
 **Přidat**  
 Přidá parametr zadáte v **název parametru**a jeho atributy typu a parametrů do **seznam parametrů**. Musíte kliknout na **přidat** přidání parametru do seznamu.  
  
 **Odebrat**  
 Odebere parametr vyberete v **seznam parametrů** ze seznamu.  
  
 **Seznam parametrů**  
 Zobrazí všechny parametry a jejich modifikátory a typy, které jsou aktuálně přidané do metody. Po přidání parametrů, bude průvodce aktualizovat **seznam parametrů** zobrazíte každý parametr s jeho modifikátor a typem.  
  
## <a name="see-also"></a>Viz také  
 [Přidání metody](../ide/adding-a-method-visual-cpp.md)   
 [IDL – atributy, Průvodce přidáním metody](../ide/idl-attributes-add-method-wizard.md)