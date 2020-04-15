---
title: 'MFC – ovládací prvky ActiveX: Přidání přizpůsobených vlastností'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: 00f7a879582bca562ce626fe224206094fd19bc7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364706"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC – ovládací prvky ActiveX: Přidání přizpůsobených vlastností

Vlastní vlastnosti se liší od vlastností zásob `COleControl` v tom, že vlastní vlastnosti nejsou již implementovány třídou. Vlastní vlastnost se používá k vystavení určitého stavu nebo vzhledu ovládacího prvku ActiveX programátorovi používajícímu ovládací prvek.

Tento článek popisuje, jak přidat vlastní vlastnost ovládacího prvku ActiveX pomocí Průvodce přidáním vlastností a vysvětluje výsledné změny kódu. Témata:

- [Přidání vlastní vlastnosti pomocí Průvodce přidáním vlastností](#_core_using_classwizard_to_add_a_custom_property)

- [Přidat změny Průvodce vlastnostmi pro vlastní vlastnosti](#_core_classwizard_changes_for_custom_properties)

Vlastní vlastnosti jsou dodávány ve čtyřech variantách implementace: Proměnná člena, Proměnná člena s oznámením, Metody get/set a Parametrizované.

- Implementace členské proměnné

   Tato implementace představuje stav vlastnosti jako členské proměnné ve třídě ovládacího prvku. Implementaci členské proměnné použijte v případě, že není důležité vědět, kdy se změní hodnota vlastnosti. Ze tří typů tato implementace vytvoří nejmenší množství kódu podpory pro vlastnost. Makro položky odeslání mapy pro implementaci členské proměnné je [DISP_PROPERTY](../mfc/reference/dispatch-maps.md#disp_property).

- Proměnná člena s implementací oznámení

   Tato implementace se skládá z členské proměnné a funkce oznámení vytvořené Průvodcem přidáním vlastnosti. Funkce oznámení je automaticky volána rozhraním po změně hodnoty vlastnosti. Proměnná člena s implementací oznámení, pokud potřebujete být upozorněni po změně hodnoty vlastnosti. Tato implementace vyžaduje více času, protože vyžaduje volání funkce. Makro položky mapy odeslání pro tuto implementaci je [DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify).

- Implementace metod get/set

   Tato implementace se skládá z dvojice členských funkcí v kontrolní třídě. Get/Set Metody implementace automaticky volá Get členské funkce, když uživatel ovládacího prvku požaduje aktuální hodnotu vlastnosti a Set členské funkce, když uživatel ovládacího prvku požaduje, aby vlastnost byla změněna. Tuto implementaci použijte, když potřebujete vypočítat hodnotu vlastnosti za běhu, ověřit hodnotu předanou uživatelem ovládacího prvku před změnou skutečné vlastnosti nebo implementovat typ vlastnosti jen pro čtení nebo zápis. Makro položky mapy odeslání pro tuto implementaci je [DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex). Následující [část: Použití Průvodce přidáním vlastností k přidání vlastní vlastnosti](#_core_using_classwizard_to_add_a_custom_property)používá vlastní vlastnost CircleOffset k předvedení této implementace.

- Parametrizovaná implementace

   Parametrizovaná implementace je podporována Průvodcem přidáním vlastností. Parametrizovaná vlastnost (někdy nazývaná pole vlastností) lze použít pro přístup k sadě hodnot prostřednictvím jedné vlastnosti ovládacího prvku. Makro položky mapy odeslání pro tuto implementaci je DISP_PROPERTY_PARAM. Další informace o implementaci tohoto typu naleznete v [tématu Implementace parametrizované vlastnosti](../mfc/mfc-activex-controls-advanced-topics.md) v článku Ovládací prvky ActiveX: Rozšířená témata.

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a>Přidání vlastní vlastnosti pomocí Průvodce přidáním vlastností

Následující postup ukazuje přidání vlastní vlastnostcircleoffset, který používá Get/Set metody implementace. Vlastní vlastnost CircleOffset umožňuje uživateli ovládacího prvku odsadit kruh od středu ohraničovacího obdélníku ovládacího prvku. Postup pro přidání vlastních vlastností s implementací než Get/Set Metody je velmi podobný.

Stejný postup lze také použít k přidání dalších vlastních vlastností, které chcete. Nahraďte název vlastní vlastnosti názvem a parametry vlastnosti CircleOffset.

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>Přidání vlastní vlastnosti CircleOffset pomocí Průvodce přidáním vlastností

1. Načtěte projekt ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klepnutím pravým tlačítkem myši na uzel rozhraní ovládacího prvku (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat vlastnost**.

   Otevře se [Průvodce přidáním vlastností](../ide/names-add-property-wizard.md).

1. Do pole **Název vlastnosti** zadejte *CircleOffset*.

1. V **souboru Typ implementace**klepněte na tlačítko Získat nebo nastavit **metody**.

1. V poli **Typ vlastnosti** vyberte **krátký**.

1. Zadejte jedinečné názvy funkcí Get a Set nebo přijměte výchozí názvy.

1. Klikněte na **Finish** (Dokončit).

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a>Přidat změny Průvodce vlastnostmi pro vlastní vlastnosti

Když přidáte vlastní vlastnost CircleOffset, Průvodce přidáním vlastností provede změny v záhlaví (. H) a provádění (. CPP) třídy ovládacích prvku.

Do souboru jsou přidány následující řádky. H, chcete-li `GetCircleOffset` deklarovat dvě volané funkce a `SetCircleOffset`:

[!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

Následující řádek je přidán do ovládacího prvku . IDL soubor:

[!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

Tento řádek přiřadí vlastnosti CircleOffset určité číslo ID převzaté z pozice metody v seznamu metod a vlastností Průvodce přidáním vlastností.

Kromě toho je do mapy odeslání přidán následující řádek (v . CPP soubor třídy ovládacího prvku) pro mapování vlastnosti CircleOffset na dvě funkce obslužné rutiny ovládacího prvku:

[!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

Nakonec implementace `GetCircleOffset` a `SetCircleOffset` funkce jsou přidány na konec ovládacího prvku . CPP. Ve většině případů upravíte Get funkce vrátit hodnotu vlastnosti. Funkce Set bude obvykle obsahovat kód, který by měl být proveden před nebo po změně vlastnosti.

[!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

Všimněte si, že Průvodce přidáním vlastností automaticky přidá volání [do funkce SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag)do těla funkce Set. Volání této funkce označí ovládací prvek jako upravený. Pokud byl ovládací prvek změněn, jeho nový stav bude uložen při uložení kontejneru. Tato funkce by měla být volána vždy, když se změní vlastnost uložená jako součást trvalého stavu ovládacího prvku.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Vlastnosti](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC – ovládací prvky ActiveX: Metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Třída COleControl](../mfc/reference/colecontrol-class.md)
