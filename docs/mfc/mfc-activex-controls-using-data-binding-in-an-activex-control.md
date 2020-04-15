---
title: 'MFC – ovládací prvky ActiveX: Použití datových vazeb v ovládacím prvku ActiveX'
ms.date: 11/19/2018
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
ms.openlocfilehash: 41ac0180242aea3143a1df2c32dc81fb18cd7dca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370784"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC – ovládací prvky ActiveX: Použití datových vazeb v ovládacím prvku ActiveX

Jedním z výkonnějších použití ovládacích prvků ActiveX je datová vazba, která umožňuje vlastnost ovládacího prvku svázat s určitým polem v databázi. Když uživatel upraví data v této vázané vlastnosti, ovládací prvek upozorní databázi a požádá o aktualizaci pole záznamu. Databáze pak upozorní řízení o úspěchu nebo neúspěchu požadavku.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

Tento článek popisuje ovládací stránku úlohy. Implementace interakce datové vazby s databází je odpovědností kontejneru ovládacího prvku. Způsob správy interakcí databáze v kontejneru je nad rámec této dokumentace. Jak připravit ovládací prvek pro datové vazby je vysvětleno ve zbytku tohoto článku.

![Koncepční diagram ovládacího prvku&#45;dat](../mfc/media/vc374v1.gif "Koncepční diagram ovládacího prvku&#45;dat") <br/>
Koncepční diagram ovládacího prvku vázaného na data

Třída `COleControl` poskytuje dvě členské funkce, které usnadňují implementaci datové vazby. První funkce [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit)se používá k vyžádání oprávnění ke změně hodnoty vlastnosti. [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged), druhá funkce, je volána po úspěšné změně hodnoty vlastnosti.

Tento článek popisuje následující témata:

- [Vytvoření vazby skladové vlastnosti](#vchowcreatingbindablestockproperty)

- [Vytvoření vypojitelné metody get/set](#vchowcreatingbindablegetsetmethod)

## <a name="creating-a-bindable-stock-property"></a><a name="vchowcreatingbindablestockproperty"></a>Vytvoření vazby skladové vlastnosti

Je možné vytvořit data vázanou vlastnost akcií, i když je pravděpodobnější, že budete chtít [vyvažovatelnou metodu get/set](#vchowcreatingbindablegetsetmethod).

> [!NOTE]
> Vlastnosti `bindable` skladu `requestedit` mají ve výchozím nastavení atributy a.

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Přidání vazby skladové vlastnosti pomocí Průvodce přidáním vlastností

1. Zahájení projektu pomocí [Průvodce ovládacím prvkem ActiveX knihovny MFC](../mfc/reference/mfc-activex-control-wizard.md).

1. Klikněte pravým tlačítkem myši na uzel rozhraní pro ovládací prvek.

   Otevře se místní nabídka.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat vlastnost**.

1. Vyberte jednu z položek z rozevíracího seznamu **Název vlastnosti.** Můžete například vybrat **text**.

   Vzhledem k tomu, **že Text** je vlastnost zásob, jsou již zkontrolovány **vazby a** atributy **requestedit.**

1. Na kartě **Atributy IDL** zaškrtněte následující políčka: **displaybind** a **defaultbind** pro přidání atributů do definice vlastnosti v projektu . IDL. Tyto atributy zviditelní ovládací prvek pro uživatele a vlastnost stock výchozí vlastnosti s houževnatá.

V tomto okamžiku může ovládací prvek zobrazit data ze zdroje dat, ale uživatel nebude moci aktualizovat datová pole. Pokud chcete, aby ovládací prvek také mohl `OnOcmCommand` aktualizovat data, změňte funkci [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) takto:

[!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

Nyní můžete vytvořit projekt, který bude registrovat ovládací prvek. Když vložíte ovládací prvek do dialogového okna, budou přidány **vlastnosti Datové pole** a **Zdroj dat** a nyní můžete vybrat zdroj dat a pole, které se zobrazí v ovládacím prvku.

## <a name="creating-a-bindable-getset-method"></a><a name="vchowcreatingbindablegetsetmethod"></a>Vytvoření vypojitelné metody get/set

Kromě metody get/set vázané na data můžete také vytvořit [vypojitelnou vlastnost .](#vchowcreatingbindablestockproperty)

> [!NOTE]
> Tento postup předpokládá, že máte projekt ovládacího prvku ActiveX, který podřcovává ovládací prvek systému Windows.

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Přidání vazby get/set metoda pomocí Průvodce přidáním vlastností

1. Načtěte projekt ovládacího prvku.

1. Na stránce **Nastavení ovládacího prvku** vyberte třídu okna pro ovládací prvek do podtřídy. Můžete například podtřídovat ovládací prvek EDIT.

1. Načtěte projekt ovládacího prvku.

1. Klikněte pravým tlačítkem myši na uzel rozhraní pro ovládací prvek.

   Otevře se místní nabídka.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat vlastnost**.

1. Do pole Název vlastnosti zadejte název **vlastnosti.** Použijte `MyProp` pro tento příklad.

1. Vyberte datový typ z rozevíracího seznamu **Typ vlastnosti.** Použijte **krátký** pro tento příklad.

1. V **souboru Typ implementace**klepněte na tlačítko Získat nebo nastavit **metody**.

1. Na kartě Atributy IDL zaškrtněte následující políčka: **bindable**, **requestedit**, **displaybind**a **defaultbind** pro přidání atributů do definice vlastnosti v projektu . IDL. Tyto atributy zviditelní ovládací prvek pro uživatele a vlastnost stock výchozí vlastnosti s houževnatá.

1. Klikněte na **Finish** (Dokončit).

1. Upravte tělo `SetMyProp` funkce tak, aby obsahovala následující kód:

   [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. Parametr předaný `BoundPropertyChanged` `BoundPropertyRequestEdit` funkcím a je dispid vlastnosti, což je parametr předaný atributu id() pro vlastnost v . IDL.

1. Upravte funkci [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) tak, aby obsahovala následující kód:

   [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. Upravte `OnDraw` funkci tak, aby obsahovala následující kód:

   [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. Do veřejné části souboru záhlaví souboru záhlaví pro třídu ovládacího prvku přidejte následující definice (konstruktory) pro členské proměnné:

   [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. Následující řádek vytvořte jako `DoPropExchange` poslední řádek ve funkci:

   [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. Upravte `OnResetState` funkci tak, aby obsahovala následující kód:

   [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. Upravte `GetMyProp` funkci tak, aby obsahovala následující kód:

   [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

Nyní můžete vytvořit projekt, který bude registrovat ovládací prvek. Když vložíte ovládací prvek do dialogového okna, budou přidány **vlastnosti Datové pole** a **Zdroj dat** a nyní můžete vybrat zdroj dat a pole, které se zobrazí v ovládacím prvku.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
