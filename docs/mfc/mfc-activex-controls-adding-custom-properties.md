---
title: 'MFC – ovládací prvky ActiveX: Přidání přizpůsobených vlastností'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: 2cc9cfa1886c6ba8e714736e0192b56bf3b154f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496418"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC – ovládací prvky ActiveX: Přidání přizpůsobených vlastností

Vlastní vlastnosti se liší od uložených vlastností v tom, že vlastní vlastnosti nejsou již implementováno prostřednictvím `COleControl` třídy. Vlastní vlastnost se používá k vystavení stavu nebo vzhled ovládacího prvku ActiveX na programátorovi, pomocí ovládacího prvku.

Tento článek popisuje, jak přidat vlastní vlastnost do ovládacího prvku ActiveX pomocí Průvodce přidáním vlastnosti a vysvětluje výsledné změny kódu. Mezi témata patří:

- [Chcete-li přidat vlastní vlastnost pomocí Průvodce přidáním vlastnosti](#_core_using_classwizard_to_add_a_custom_property)

- [Přidat Průvodce vlastností změny provedené u vlastní vlastnosti](#_core_classwizard_changes_for_custom_properties)

Vlastní vlastnosti se dělí na čtyři typy implementace: členskou proměnnou, členské proměnné s parametrizované, oznámení a metody Get/Set.

- Implementace členské proměnné

   Tato implementace představuje stav vlastnosti jako členskou proměnnou v třídě ovládacího prvku. Členské proměnné implementace použijte, pokud to není důležité vědět, když se změní hodnota vlastnosti. Ze tří typů vytvoří tato implementace minimální množství kódu podpory pro vlastnost. Je makro položky mapy odeslání pro členské proměnné implementace [DISP_PROPERTY](../mfc/reference/dispatch-maps.md#disp_property).

- Členské proměnné s implementací oznámení

   Tato implementace se skládá z členské proměnné a funkce oznámení vytvořený pomocí průvodce přidat vlastnost. Funkce oznámení je automaticky volá se rozhraním po změně hodnoty vlastnosti. Používejte členskou proměnnou s implementací oznámení budete potřebovat, abyste dostávali oznámení po změně hodnoty vlastnosti. Tato implementace vyžaduje více času, protože vyžaduje volání funkce. Je makro položky mapy odeslání pro tuto implementaci [DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify).

- Implementace metody Get/Set

   Tato implementace se skládá z dvojice členské funkce ve třídě ovládacího prvku. Implementace metody Get/Set automaticky volá člen Get funkci ovládacího prvku uživatel požádá o aktuální hodnota vlastnosti a členskou funkci Set, pokud ovládacího prvku uživatel požaduje, aby byla změněna vlastnost. Tuto implementaci používejte, když potřebujete vypočítat hodnotu vlastnosti za běhu, ověřte hodnotu předanou uživatelem ovládacího prvku před změnou skutečné vlastnost, nebo implementovat typ vlastnosti jen pro čtení nebo zápisu –. Je makro položky mapy odeslání pro tuto implementaci [DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex). V následující části [pomocí Průvodce přidáním vlastnosti lze přidat vlastní vlastnost](#_core_using_classwizard_to_add_a_custom_property), používá vlastní vlastnost CircleOffset k předvedení toho tuto implementaci.

- Parametrizované implementace

   Parametrizované implementace podporuje Průvodce přidáním vlastnosti. Parametrizovaná vlastnost (říká se jim vlastnost pole) lze použít pro přístup k sadě hodnot prostřednictvím jedné vlastnosti ovládacího prvku. DISP_PROPERTY_PARAM je makro položky mapy odeslání pro tuto implementaci. Další informace o implementaci tohoto typu, najdete v části [implementace Parametrizovaná vlastnost](../mfc/mfc-activex-controls-advanced-topics.md) v následujícím článku – ovládací prvky ActiveX: Advanced témata.

##  <a name="_core_using_classwizard_to_add_a_custom_property"></a> Použití přidat průvodce vlastností můžete přidat vlastní vlastnost

Následující postup ukazuje přidání vlastnosti do vlastního CircleOffset, který používá implementaci metody Get/Set. Vlastní vlastnost CircleOffset umožňuje uživateli ovládacího prvku posun na kolečko v centru ohraničující obdélník ovládacího prvku. Postup pro přidání vlastních vlastností s implementací jiného než metody Get/Set se velmi podobné.

Stejný postup lze také přidat další vlastní požadované vlastnosti. Nahraďte název vaší vlastní vlastnosti pro název vlastnosti CircleOffset a parametry.

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>Chcete-li přidat vlastní vlastnost CircleOffset pomocí Průvodce přidáním vlastnosti

1. Načtení projektu ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klikněte pravým tlačítkem na uzel rozhraní pro ovládací prvek (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat vlastnost**.

   Tím se otevře [Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md).

1. V **název vlastnosti** zadejte *CircleOffset*.

1. Pro **typ implementace**, klikněte na tlačítko **metody Get/Set**.

1. V **typ vlastnosti** vyberte **krátký**.

1. Zadejte jedinečné názvy pro získání a nastavení funkce nebo přijměte výchozí názvy.

9. Klikněte na tlačítko **Dokončit**.

##  <a name="_core_classwizard_changes_for_custom_properties"></a> Přidat Průvodce změny vlastností pro vlastní vlastnosti

Když přidáte vlastní vlastnost CircleOffset, Průvodce přidáním vlastnosti změní záhlaví (. H) a implementace (. Soubory CPP) třídy ovládacího prvku.

Následující řádky se přidají do. H soubor pro deklaraci dvě funkce volané `GetCircleOffset` a `SetCircleOffset`:

[!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

Následující řádek je přidán do ovládacího prvku. Soubor IDL:

[!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

Tento řádek přiřadí vlastnost CircleOffset konkrétní identifikační číslo, na základě pozice metody v seznamu metod a vlastností Průvodce přidáním vlastnosti.

Kromě toho se přidá následující řádek do mapy odeslání (v. Soubor CPP třídy ovládacího prvku) pro mapování vlastnost CircleOffset na dvě funkce obslužná rutina ovládacího prvku:

[!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

Nakonec implementace `GetCircleOffset` a `SetCircleOffset` funkce jsou přidány na konec objektu ovládacího prvku. Soubor CPP. Ve většině případů se upravit funkci Get vrátit hodnotu vlastnosti. Funkci Set bude obvykle obsahovat kód, který má být provedena před nebo po změně vlastnosti.

[!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

Všimněte si, že Průvodce přidáním vlastnosti automaticky přidá volání do [SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag), do těla funkce Set. Volání této funkce označuje ovládací prvek, jako jsou změny. Pokud ovládací prvek byl změněn, při uložení kontejneru se uloží jeho nového stavu. Při změně hodnoty vlastnosti, uložit jako součást trvalý stav ovládacího prvku, lze volat tuto funkci.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Vlastnosti](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC – ovládací prvky ActiveX: Metody](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl – třída](../mfc/reference/colecontrol-class.md)
