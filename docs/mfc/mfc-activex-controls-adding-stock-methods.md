---
title: 'MFC – ovládací prvky ActiveX: Přidání uložených metod | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b42907273423d69ed93df5700b33556047338fe2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391423"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC – ovládací prvky ActiveX: Přidání uložených metod

Základní metoda se liší od vlastní metodu v tom, že je již implementováno třídou [COleControl](../mfc/reference/colecontrol-class.md). Například `COleControl` obsahuje předdefinované členskou funkci, která podporuje metodu aktualizace pro ovládací prvek. Položka mapy odeslání pro tato základní metoda je DISP_STOCKFUNC_REFRESH.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

`COleControl` podporuje dvě základní metody: DoClick a aktualizace. Aktualizace je vyvolán uživatelem ovládacího prvku se okamžitě aktualizovat vzhled ovládacího prvku; DoClick se má provést, klikněte na tlačítko ovládacího prvku vyvolá událost.

|Metoda|Zápis do mapy odbavení|Komentář|
|------------|------------------------|-------------|
|`DoClick`|**(DISP_STOCKPROP_DOCLICK)**|Vyvolá událost Click.|
|`Refresh`|**(DISP_STOCKPROP_REFRESH)**|Aktualizuje se okamžitě vzhled ovládacího prvku.|

##  <a name="_core_adding_a_stock_method_using_classwizard"></a> Přidání pomocí vyvolá integrovaná metoda Průvodce přidáním metody

Přidání uložených metody je jednoduché použití [Průvodce přidáním metody](../ide/add-method-wizard.md). Následující postup ukazuje přidání metody aktualizace na ovládací prvek vytvořili pomocí Průvodce ovládacím prvkem ActiveX knihovny MFC.

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Chcete-li přidat základní metoda obnovení pomocí Průvodce přidáním metody

1. Načtení projektu ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klikněte pravým tlačítkem na uzel rozhraní pro ovládací prvek (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat metodu**.

     Otevře se Průvodce přidáním metody.

1. V **název metody** klikněte **aktualizovat**.

1. Klikněte na tlačítko **Dokončit**.

##  <a name="_core_classwizard_changes_for_stock_methods"></a> Přidejte metodu Průvodce změny pro uložených metod

Protože základní metoda aktualizace je podporována základní třídou ovládacího prvku, **Průvodce přidáním metody** deklarace třídy ovládacího prvku nijak nezmění. Přidá položku pro metodu do mapy odbavení ovládacího prvku a jeho. Soubor IDL. Následující řádek je přidávají do mapy odbavení ovládacího prvku, v jeho provádění (. Soubor CPP):

[!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

Díky tomu metodu aktualizace k dispozici uživatelům ovládacího prvku.

Následující řádek je přidán do ovládacího prvku. Soubor IDL:

[!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

Tento řádek přiřadí způsob aktualizace na konkrétní číslo ID.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

