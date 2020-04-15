---
title: 'MFC – ovládací prvky ActiveX: Přidání vlastních metod'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: 88d486248eab5d980463764db34bf40b05b830dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364712"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>MFC – ovládací prvky ActiveX: Přidání vlastních metod

Vlastní metody se liší od skladových metod `COleControl`v tom, že již nejsou implementovány . Je nutné zadat implementaci pro každou vlastní metodu, kterou přidáte do ovládacího prvku.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

Uživatel ovládacího prvku ActiveX může kdykoli volat vlastní metodu k provádění akcí specifických pro ovládací prvek. Položka mapy odeslání pro vlastní metody je formuláře DISP_FUNCTION.

## <a name="adding-a-custom-method-with-the-add-method-wizard"></a><a name="_core_adding_a_custom_method_with_classwizard"></a>Přidání vlastní metody pomocí Průvodce přidáním metody

Následující postup ukazuje přidání vlastní metody PtInCircle do kódu kostry ovládacího prvku ActiveX. PtInCircle určuje, zda jsou souřadnice předané ovládacímu prvku uvnitř nebo vně kruhu. Stejný postup lze také přidat další vlastní metody. Nahraďte název vlastní metody a její parametry názvem a parametry metody PtInCircle.

> [!NOTE]
> Tento příklad `InCircle` používá funkci z článku Události. Další informace o této funkci naleznete v článku [Ovládací prvky ActiveX knihovny MFC: Přidání vlastních událostí do ovládacího prvku ActiveX](../mfc/mfc-activex-controls-adding-custom-events.md).

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>Přidání vlastní metody PtInCircle pomocí Průvodce přidáním metody

1. Načtěte projekt ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klepnutím pravým tlačítkem myši na uzel rozhraní ovládacího prvku (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat metodu**.

   Tím se otevře Průvodce přidáním metody.

1. Do pole **Název metody** zadejte *PtInCircle*.

1. Do pole **Vnitřní název** zadejte název interní funkce metody nebo použijte výchozí hodnotu (v tomto případě *PtInCircle).*

1. V poli **Návratový typ** klikněte na **VARIANT_BOOL** pro návratový typ metody.

1. Pomocí ovládacích prvků **Typ parametru** a **Název parametru** přidejte parametr s názvem *xCoord* (typ *OLE_XPOS_PIXELS*).

1. Pomocí ovládacích prvků **Typ parametru** a **Název parametru** přidejte parametr s názvem *yCoord* (typ *OLE_YPOS_PIXELS*).

1. Klikněte na **Finish** (Dokončit).

## <a name="add-method-wizard-changes-for-custom-methods"></a><a name="_core_classwizard_changes_for_custom_methods"></a>Přidat změny Průvodce metodou pro vlastní metody

Když přidáte vlastní metodu, Průvodce přidáním metody provede některé změny v záhlaví třídy ovládacího prvku (. H) a provádění (. CPP). Následující řádek je přidán do deklarace mapy odeslání v záhlaví třídy ovládacího prvku (. H) soubor:

[!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

Tento kód deklaruje `PtInCircle`obslužnou rutinu metody odeslání volanou . Tuto funkci může volat uživatel ovládacího `PtInCircle`prvku pomocí externího názvu .

Následující řádek je přidán do ovládacího prvku . IDL soubor:

[!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

Tento řádek přiřadí metodě `PtInCircle` určité číslo ID, pozici metody v seznamu metod a vlastností Průvodce přidáním metody. Vzhledem k tomu, že k přidání vlastní metody byl použit Průvodce přidáním metody přidání, byla položka pro metodu automaticky přidána do projektu . IDL.

Kromě toho následující řádek, který se nachází v implementaci (. CPP) třídy řízení, je přidán do mapy dispečera ovládacího prvku:

[!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

Makro DISP_FUNCTION mapuje `PtInCircle` metodu na funkci `PtInCircle`obslužné rutiny ovládacího prvku , deklaruje návratový `PtInCircle` **typ,** který má být VARIANT_BOOL , a deklaruje dva parametry typu **VTS_XPOS_PIXELS** a **VTS_YPOSPIXELS,** které mají být předány .

Nakonec Průvodce přidáním metody přidá `CSampleCtrl::PtInCircle` funkci se zakázaným inzerováním do dolní části implementace ovládacího prvku (. CPP). Aby `PtInCircle` fungovala tak, jak již bylo uvedeno výše, musí být upravena takto:

[!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[Ikony prohlížeče zobrazení tříd a objektů](/visualstudio/ide/class-view-and-object-browser-icons)
