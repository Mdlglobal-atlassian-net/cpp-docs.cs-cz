---
title: 'Ovládací prvky MFC ActiveX: Použití datových vazeb v ovládacím prvku ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab5195cc2381e515688182ad73452b07afd06b98
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353270"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC – ovládací prvky ActiveX: Použití datových vazeb v ovládacím prvku ActiveX
Jedno z výkonnější použití ovládacích prvků ActiveX je datovou vazbu, která umožňuje vlastnost ovládacího prvku, který má být svázána s konkrétní pole v databázi. Když uživatel upravuje data v této vázané vlastnosti, upozorní ovládacího prvku databáze a požadavky aktualizovat pole záznamu. Databáze poté oznámí kontrolu nad úspěch nebo selhání žádosti.  
  
 Tento článek se zabývá řízení straně vaším úkolem. Implementace vazby dat interakce s databází má na starosti kontejneru ovládacího prvku. Jak spravovat interakce databáze v vašeho kontejneru je nad rámec této dokumentace. Jak připravit pro datovou vazbu ovládacího prvku je vysvětleno v zbývající části tohoto článku.  
  
 ![Koncepční diagram dat.&#45;vázaný ovládací prvek](../mfc/media/vc374v1.gif "vc374v1")  
Koncepční Diagram ovládacího prvku typu vázané na Data  
  
 `COleControl` Třída poskytuje dva členské funkce, které datové vazby jednoduchý proces pro implementaci. První funkce [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit), slouží k vyžádání oprávnění ke změně hodnoty vlastnosti. [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged), druhý funkce je volána po hodnotu vlastnosti se úspěšně změnila.  
  
 Tento článek obsahuje následující témata:  
  
-   [Vytváření vazbu uložených vlastností](#vchowcreatingbindablestockproperty)  
  
-   [Vytváření vazbu Get/Set – metoda](#vchowcreatingbindablegetsetmethod)  
  
##  <a name="vchowcreatingbindablestockproperty"></a> Vytváření vazbu uložených vlastností  
 Je možné vytvořit uložených vlastností vázané na data, i když je pravděpodobnější, že budete chtít [vazbu get/set – metoda](#vchowcreatingbindablegetsetmethod).  
  
> [!NOTE]
>  Uložené vlastnosti mají **vazbu** a **requestedit –** atributy ve výchozím nastavení.  
  
#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Chcete-li přidat vazbu uložených vlastností pomocí Průvodce přidáním vlastnosti  
  
1.  Zahájení projektu pomocí [Průvodce ovládacím prvkem ActiveX knihovny MFC](../mfc/reference/mfc-activex-control-wizard.md).  
  
2.  Klikněte pravým tlačítkem na uzel rozhraní pro vlastní ovládací prvek.  
  
     Otevře se místní nabídky.  
  
3.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidat vlastnost**.  
  
4.  Vyberte jeden ze záznamů z **název vlastnosti** rozevíracího seznamu. Například můžete vybrat **Text**.  
  
     Protože **Text** je uložených vlastností **vazbu** a **requestedit –** atributy jsou již zaškrtnuté.  
  
5.  Vyberte z následujících zaškrtávacích políček **IDL – atributy** karta: **displaybind** a **defaultbind –** přidat atributy pro definování vlastnosti v projektu. IDL soubor. Tyto atributy zviditelnit ovládací prvek pro uživatele a proveďte uložených vlastností výchozí vlastnost pro vazbu.  
  
 V tomto okamžiku vlastního ovládacího prvku můžete zobrazit data ze zdroje dat, ale uživatel nebude moct aktualizovat datová pole. Pokud chcete, aby ovládací prvek také se moct aktualizovat data, změňte `OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) funkce vypadat takto:  
  
 [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
 Teď můžete sestavit projekt, který bude zaregistrovat ovládací prvek. Při vložení ovládacího prvku v dialogovém okně, **datové pole** a **zdroj dat** vlastnosti bude byly přidány a teď si můžete vybrat zdroj dat a pole pro zobrazení v ovládacím prvku.  
  
##  <a name="vchowcreatingbindablegetsetmethod"></a> Vytváření vazbu Get/Set – metoda  
 Kromě vázané na data Metoda get nebo nastavení, můžete také vytvořit [vazbu uložených vlastností](#vchowcreatingbindablestockproperty).  
  
> [!NOTE]
>  Tento postup předpokládá, že máte ovládacího prvku ActiveX projektu této podtřídy ovládacího prvku Windows.  
  
#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Chcete-li přidat vazbu get/set metodu, pomocí Průvodce přidáním vlastnosti  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  Na **nastavení řízení** vyberte třídu okna pro ovládací prvek pro podtřídy. Například můžete chtít podtřídami ovládací prvek upravit.  
  
3.  Načtení projektu ovládacího prvku.  
  
4.  Klikněte pravým tlačítkem na uzel rozhraní pro vlastní ovládací prvek.  
  
     Otevře se místní nabídky.  
  
5.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidat vlastnost**.  
  
6.  Zadejte název vlastnosti v **název vlastnosti** pole. Použití `MyProp` v tomto příkladu.  
  
7.  Vyberte datový typ z **typ vlastnosti** rozevíracího seznamu. Použití **krátké** v tomto příkladu.  
  
8.  Pro **typem implementace**, klikněte na tlačítko **metody Get/Set**.  
  
9. Zaškrtněte následující zaškrtávací políčka na kartě IDL – atributy: **vazbu**, **requestedit –**, **displaybind**, a **defaultbind –** přidat atributy pro definování vlastnosti v projektu. IDL soubor. Tyto atributy zviditelnit ovládací prvek pro uživatele a proveďte uložených vlastností výchozí vlastnost pro vazbu.  
  
10. Klikněte na tlačítko **Dokončit**.  
  
11. Upravit text `SetMyProp` fungovat tak, aby obsahoval následující kód:  
  
     [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]  
  
12. Parametr předaný `BoundPropertyChanged` a `BoundPropertyRequestEdit` funkce je dispid vlastnosti, která je předán do atribut id() pro vlastnost v parametr. IDL soubor.  
  
13. Změnit [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) fungovat tak, aby obsahovala následující kód:  
  
     [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
14. Změnit `OnDraw` fungovat tak, aby obsahoval následující kód:  
  
     [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]  
  
15. Do části veřejný soubor hlaviček třídy ovládacího prvku záhlaví souboru přidejte následující definice (konstruktory) pro členské proměnné:  
  
     [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]  
  
16. Zkontrolujte následující řádek na posledním řádku `DoPropExchange` funkce:  
  
     [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]  
  
17. Změnit `OnResetState` fungovat tak, aby obsahoval následující kód:  
  
     [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]  
  
18. Změnit `GetMyProp` fungovat tak, aby obsahoval následující kód:  
  
     [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]  
  
 Teď můžete sestavit projekt, který bude zaregistrovat ovládací prvek. Při vložení ovládacího prvku v dialogovém okně, **datové pole** a **zdroj dat** vlastnosti bude byly přidány a teď si můžete vybrat zdroj dat a pole pro zobrazení v ovládacím prvku.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)   

