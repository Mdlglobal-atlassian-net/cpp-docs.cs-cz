---
title: 'MFC – ovládací prvky ActiveX: Použití datových vazeb v ovládacím prvku ActiveX'
ms.date: 09/12/2018
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
ms.openlocfilehash: 9efac8ba0889d648def622ca045b9398c8eeef11
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518486"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC – ovládací prvky ActiveX: Použití datových vazeb v ovládacím prvku ActiveX

Jednou z výkonnější používá ovládací prvky ActiveX je datové vazby, který povolí vlastnost ovládacího prvku, který má být svázána s konkrétní pole v databázi. Když uživatel změní data v tomto vázané vlastnosti, upozorní ovládací prvek databáze a požadavky aktualizovat pole záznamu. Databáze upozorní ovládací prvek úspěch nebo selhání požadavku.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

Tento článek popisuje úlohy na straně ovládacího prvku. Implementace interakcích vazeb dat s databází zodpovídá za kontejnerem ovládacího prvku. Jak spravovat interakce databáze ve vašem kontejneru je nad rámec této dokumentace. Jak připravit ovládacího prvku pro vytváření datových vazeb jsou vysvětleny v zbývající část tohoto článku.

![Koncepční schéma celé datové&#45;vázaného ovládacího prvku](../mfc/media/vc374v1.gif "vc374v1") koncepční Diagram ovládací prvek vázaný na Data

`COleControl` Třída obsahuje dva členské funkce, které usnadňují vytváření datových vazeb jednoduchý proces k implementaci. První funkce [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit), slouží k vyžádání oprávnění ke změně hodnoty vlastnosti. [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged), druhá funkce se volá, když úspěšně změně hodnoty vlastnosti.

Tento článek obsahuje následující témata:

- [Vytvoření s možností vazby uložených vlastností](#vchowcreatingbindablestockproperty)

- [Vytvoření s možností vazby Get/Set – metoda](#vchowcreatingbindablegetsetmethod)

##  <a name="vchowcreatingbindablestockproperty"></a> Vytvoření s možností vazby uložených vlastností

Je možné vytvořit uložených vlastností vázané na data, i když je pravděpodobnější, že můžete [umožňujících vazbu get/set – metoda](#vchowcreatingbindablegetsetmethod).

> [!NOTE]
> Uložené vlastnosti mají `bindable` a `requestedit` atributy ve výchozím nastavení.

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Chcete-li přidat vazbu uložených vlastností pomocí Průvodce přidáním vlastnosti

1. Začít projektu používat [Průvodce ovládacím prvkem MFC ActiveX](../mfc/reference/mfc-activex-control-wizard.md).

1. Klikněte pravým tlačítkem na uzel rozhraní ovládacího prvku.

   Tím se otevře v místní nabídce.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat vlastnost**.

1. Vyberte jednu z položek **název vlastnosti** rozevíracího seznamu. Například můžete vybrat **Text**.

   Protože **Text** je uložených vlastností **umožňujících vazbu** a **requestedit –** atributy jsou již zaškrtnuté.

1. Vyberte z následujících políček **IDL – atributy** kartu: **displaybind** a **defaultbind** a přidat atributy v definici vlastnosti v projektu. Soubor IDL. Tyto atributy Zviditelněte ovládací prvek pro uživatele a zkontrolujte výchozí vázanou vlastnost uložených vlastností.

V tuto chvíli váš ovládací prvek mohl zobrazit data ze zdroje dat, ale uživatel nebude možné aktualizovat datová pole. Pokud chcete, aby ovládací prvek také umožnit aktualizaci dat, změňte `OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) funkce vypadat takto:

[!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

Nyní můžete vytvořit projekt, který se zaregistrujte ovládací prvek. Když vložíte ovládací prvek v dialogovém okně **datové pole** a **zdroj dat** vlastnosti se nepřidaly a teď můžete vybrat zdroj dat a pole, které chcete zobrazit v ovládacím prvku.

##  <a name="vchowcreatingbindablegetsetmethod"></a> Vytvoření s možností vazby Get/Set – metoda

Kromě vázaný na data získá nebo nastaví metodu, můžete také vytvořit [umožňujících vazbu uložených vlastností](#vchowcreatingbindablestockproperty).

> [!NOTE]
> Tento postup předpokládá, že máte ovládacího prvku ActiveX projektu, která je podtřídou ovládací prvek Windows.

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Přidání metody get/set-umožňujících vazbu pomocí Průvodce přidáním vlastnosti

1. Načtení projektu ovládacího prvku.

1. Na **nastavení** vyberte třídu okna pro ovládací prvek do podtříd. Například můžete chtít podtřídy ovládacího prvku pro úpravy.

1. Načtení projektu ovládacího prvku.

1. Klikněte pravým tlačítkem na uzel rozhraní ovládacího prvku.

   Tím se otevře v místní nabídce.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat vlastnost**.

1. Zadejte název vlastnosti v **název vlastnosti** pole. Použití `MyProp` pro účely tohoto příkladu.

1. Vyberte datový typ z **typ vlastnosti** rozevíracího seznamu. Použití **krátký** pro účely tohoto příkladu.

1. Pro **typ implementace**, klikněte na tlačítko **metody Get/Set**.

1. Zaškrtněte následující políčka na kartě Atributy IDL: **umožňujících vazbu**, **requestedit –**, **displaybind**, a **defaultbind** přidat atributy v definici vlastnosti v projektu. Soubor IDL. Tyto atributy Zviditelněte ovládací prvek pro uživatele a zkontrolujte výchozí vázanou vlastnost uložených vlastností.

1. Klikněte na tlačítko **Dokončit**.

1. Upravit text `SetMyProp` fungovat tak, aby obsahoval následující kód:

   [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. Parametr předána `BoundPropertyChanged` a `BoundPropertyRequestEdit` funkce je hodnota dispid vlastnost, která je parametr předaný pro vlastnost v atributu id(). Soubor IDL.

1. Upravit [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) fungovat tak, aby obsahovala následující kód:

   [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. Upravit `OnDraw` fungovat tak, aby obsahoval následující kód:

   [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. Do veřejné sekce souboru hlaviček hlavičkový soubor pro třídy vašeho ovládacího prvku přidejte následující definice (konstruktory) pro členské proměnné:

   [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. Zkontrolujte následující řádek na posledním řádku `DoPropExchange` funkce:

   [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. Upravit `OnResetState` fungovat tak, aby obsahoval následující kód:

   [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. Upravit `GetMyProp` fungovat tak, aby obsahoval následující kód:

   [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

Nyní můžete vytvořit projekt, který se zaregistrujte ovládací prvek. Když vložíte ovládací prvek v dialogovém okně **datové pole** a **zdroj dat** vlastnosti se nepřidaly a teď můžete vybrat zdroj dat a pole, které chcete zobrazit v ovládacím prvku.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

