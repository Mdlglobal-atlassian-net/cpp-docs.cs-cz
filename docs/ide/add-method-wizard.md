---
title: Průvodce přidáním metody | Dokumentace Microsoftu
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
ms.openlocfilehash: 45c3b0ca9a3e6c88e4ae40a5eb52aeb3223d2860
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397297"
---
# <a name="add-method-wizard"></a>Průvodce přidáním metody

Tohoto průvodce použijte k přidání metody rozhraní. V závislosti na typu projektu nebo ke kterému je přidání metody typu rozhraní Průvodce zobrazí různé možnosti.

## <a name="names"></a>Názvy

- **Návratový typ**

   Datový typ vrácený metodou. `HRESULT` doporučuje se pro všechny typy rozhraní, protože poskytuje standardní způsob, jak vrátit chyby.

   |Typ rozhraní|Popis|
   |--------------------|-----------------|
   |Duální rozhraní|`HRESULT`. Jakákoliv.|
   |Vlastní rozhraní|`HRESULT`. Jakákoliv.|
   |Vlastní místní rozhraní|Zadejte vlastní návratový typ nebo vyberte ze seznamu.|
   |Dispinterface|Zadejte vlastní návratový typ nebo vyberte ze seznamu.|
   |Dispinterface ovládací prvek ActiveX knihovny MFC|Pokud implementujete základní metodu, je nastavena na hodnotu odpovídající návratový typ a nejde změnit. Pokud vyberete metodu z **název metody** seznamu a klikněte na tlačítko **vlastní** pod **vyberte typ metody**, vyberte typ vrácené hodnoty ze seznamu.|

- **Název metody**

   Nastaví název metody.

   |Typ rozhraní|Popis|
   |--------------------|-----------------|
   |Duální rozhraní ATL, vlastní rozhraní a vlastní místní rozhraní|Zadejte vlastní název metody.|
   |Dispinterface knihovny MFC|Zadejte název vlastní metody nebo vyberte název navrhované metody ze seznamu. Pokud název vyberete ze seznamu, zobrazí se v odpovídající hodnotu **návratový typ** pole a to se nedá měnit.|
   |Dispinterface ovládací prvek ActiveX knihovny MFC|Zadejte vlastní nebo vyberte některý z uložených metod [DoClick](../mfc/reference/colecontrol-class.md#doclick) a [aktualizovat](../mfc/reference/colecontrol-class.md#refresh). Zobrazit [knihovny MFC – ovládací prvky ActiveX: Přidání uložených metod](../mfc/mfc-activex-controls-adding-stock-methods.md) Další informace.|

- **Typ metody**

   K dispozici pouze pro ovládací prvky ActiveX knihovny MFC. Pokud zadáte název metody ve **název metody** pole, namísto výběru metody ze seznamu, je toto políčko není k dispozici.

   Pokud vyberete jednu z metod v **název metody** seznamu, zvolte základní nebo vlastní implementaci.

   |Typ metody|Popis|
   |-----------------|-----------------|
   |**Stock**|Výchozí nastavení Vloží základní implementaci metody, vyberte v **název metody** seznamu. **Návratový typ** nejde změnit, pokud vyberete **akcie**.|
   |**Vlastní**|Vloží zástupné procedury implementace metody ve vybrané **název metody** seznamu. Pro typy vlastní metodu, můžete zadat vlastní návratový typ, nebo můžete vybrat jednu z **návratový typ** seznamu.|

- **Interní název**

   K dispozici pouze pro vlastní metody přidat odesílajícího rozhraní knihovny MFC. Nastaví název použitý v mapa odeslání, soubor hlaviček (.h) a soubor implementace (.cpp). Ve výchozím nastavení, tento název je stejný jako **název metody**. Můžete změnit název metody, pokud pracujete s odesílajícího rozhraní knihovny MFC nebo pokud chcete přidat vlastní metodu odesílajícího rozhraní ovládací prvek ActiveX knihovny MFC.

   |Typ rozhraní|Popis|
   |--------------------|-----------------|
   |Duální rozhraní ATL, vlastní rozhraní a vlastní místní rozhraní|Není k dispozici|
   |Dispinterface knihovny MFC|Ve výchozím nastavení má název metody. Můžete upravit interní název.|
   |Dispinterface ovládací prvek ActiveX knihovny MFC|Můžete nastavit jenom interní název vlastních metod. Uložených metod nepoužívejte interní název.|

- **Atributy parametru**

   Nastaví další atributy pro zadaný v parametru **název parametru**.

   |Atribut parametru|Popis|Povolené kombinace|
   |-------------------------|-----------------|--------------------------|
   |**V**|Označuje, že parametr je předán z volající procedury do volané procedury.|**v** pouze<br /><br /> **v** a **navýšení kapacity**|
   |**navýšení kapacity**|Označuje, že parametr ukazatel se vrátí z volané procedury do volající procedury (ze serveru do klienta).|**navýšení kapacity** pouze<br /><br /> **v** a **navýšení kapacity**<br /><br /> **navýšení kapacity** a **retval**|
   |**retval**|Označuje, že parametr přijímá návratovou hodnotu člena.|**retval** a na víc systémů|

- **Typ parametru**

   Nastaví datový typ parametru. Vyberte typ ze seznamu.

- **Název parametru**

   Nastaví název parametru předávání metodu. Po zadání názvu, musíte kliknout na **přidat** ho přidat do seznamu parametrů, které budou předány metodě. Pokud nezadáte název parametru, Průvodce přeskočí všechny atributy parametru (pouze ATL) nebo **typ parametru** výběry.

   Po kliknutí na **přidat**, zobrazí se název parametru v **seznam parametrů**.

   > [!Note]
   > Pokud zadáte název parametru a potom klikněte na tlačítko **Dokončit** před kliknutím na **přidat**, není parametr metody přidán. Musíte najít metodu a ručně vložit parametr.

- **Add**

   Přidá parametr, který jste zadali v **název parametru**a její typ a atributy parametru do **seznam parametrů**. Musíte kliknout na **přidat** přidání parametru do seznamu.

- **odebrat**

   Odstraní parametr vyberete v **seznam parametrů** ze seznamu.

- **Seznam parametrů**

   Zobrazí všechny parametry a jejich typy, které jsou právě přidané do metody a modifikátory. Jak budete přidávat parametry, průvodce aktualizuje **seznam parametrů** zobrazíte každý parametr s jeho modifikátor a typem.

## <a name="see-also"></a>Viz také

[Přidání metody](../ide/adding-a-method-visual-cpp.md)<br/>
[IDL – atributy, Průvodce přidáním metody](../ide/idl-attributes-add-method-wizard.md)