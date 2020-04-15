---
title: 'MFC – ovládací prvky ActiveX: Přidání uložených metod'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: ec59ccc0cbd48fc3114eb2dc0833dd3dd65691de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364675"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC – ovládací prvky ActiveX: Přidání uložených metod

Skladová metoda se liší od vlastní metody v tom, že je již implementována třídou [COleControl](../mfc/reference/colecontrol-class.md). Například `COleControl` obsahuje předdefinovanou členská funkci, která podporuje metodu Refresh pro ovládací prvek. Položka mapy odeslání pro tuto metodu zásob je DISP_STOCKFUNC_REFRESH.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

`COleControl`podporuje dvě skladové metody: DoClick a Refresh. Aktualizace je vyvolána uživatelem ovládacího prvku k okamžité aktualizaci vzhledu ovládacího prvku; DoClick je vyvolána k požáru ovládacího prvku Click událost.

|Metoda|Položka mapy odeslání|Poznámka|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK( )**|Spustí událost Click.|
|`Refresh`|**DISP_STOCKPROP_REFRESH( )**|Okamžitě aktualizuje vzhled ovládacího prvku.|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a>Přidání skladové metody pomocí Průvodce přidáním metody

Přidání skladové metody je jednoduché pomocí [Průvodce přidáním metody](../ide/add-method-wizard.md). Následující postup ukazuje přidání metody Refresh do ovládacího prvku vytvořeného pomocí Průvodce ovládacím prvkem ActiveX knihovny MFC.

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Přidání metody aktualizace na skladě pomocí Průvodce přidáním metody

1. Načtěte projekt ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klepnutím pravým tlačítkem myši na uzel rozhraní ovládacího prvku (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat metodu**.

   Tím se otevře Průvodce přidáním metody.

1. V poli **Název metody** klepněte na tlačítko **Aktualizovat**.

1. Klikněte na **Finish** (Dokončit).

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a>Přidat změny Průvodce metodou pro skladové metody

Vzhledem k tomu, že metoda aktualizace zásob je podporována základní třídou ovládacího prvku, **Průvodce přidáním metody** žádným způsobem nezmění deklaraci třídy ovládacího prvku. Přidá položku pro metodu do mapy odeslání ovládacího prvku a do jeho . IDL. Následující řádek je přidán do mapy odeslání ovládacího prvku, který se nachází v jeho implementaci (. CPP) soubor:

[!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

Tím je metoda Refresh k dispozici uživatelům ovládacího prvku.

Následující řádek je přidán do ovládacího prvku . IDL soubor:

[!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

Tento řádek přiřadí metodě Refresh určité číslo ID.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
