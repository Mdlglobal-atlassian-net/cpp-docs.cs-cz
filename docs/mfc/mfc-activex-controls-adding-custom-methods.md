---
title: 'MFC – ovládací prvky ActiveX: Přidání vlastních metod'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: 4f5a7dc844d80ae94df8af7c0b2eea141376f9e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160143"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>MFC – ovládací prvky ActiveX: Přidání vlastních metod

Vlastní metody se liší od uložených metod, nejsou již implementováno prostřednictvím `COleControl`. Musíte zadat implementaci pro jednotlivé vlastní metody, které přidáte do ovládacího prvku.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

Jako uživatel ovládacího prvku ActiveX lze zavolat vlastní metodu kdykoli provádět akce specifické pro ovládací prvek. Položka mapy odeslání pro vlastní metody je DISP_FUNCTION ve formuláři.

##  <a name="_core_adding_a_custom_method_with_classwizard"></a> Přidání vlastní metody s Průvodce přidáním metody

Následující postup ukazuje přidání ptincircle – vlastní metoda kostru kódu ovládacího prvku ActiveX. Ptincircle – Určuje, zda jsou souřadnice předaný ovládací prvek uvnitř nebo vně kruhu. Stejný postup lze také přidat další vlastní metody. Nahraďte název vaší vlastní metodu a jeho parametry pro název metody ptincircle – a parametry.

> [!NOTE]
>  V tomto příkladu `InCircle` funkce z článku události. Další informace o této funkci najdete v článku [knihovny MFC – ovládací prvky ActiveX: Přidání vlastních událostí do ovládacího prvku ActiveX](../mfc/mfc-activex-controls-adding-custom-events.md).

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>Chcete-li přidat ptincircle – vlastní metoda pomocí Průvodce přidáním metody

1. Načtení projektu ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klikněte pravým tlačítkem na uzel rozhraní pro ovládací prvek (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat metodu**.

   Otevře se Průvodce přidáním metody.

1. V **název metody** zadejte *ptincircle –*.

1. V **interní název** zadejte název metody vnitřní funkce nebo použijte výchozí hodnotu (v tomto případě *ptincircle –*).

1. V **návratový typ** klikněte **VARIANT_BOOL** pro návratový typ metody.

1. Použití **typ parametru** a **název parametru** ovládací prvky, přidejte parametr s názvem *xCoord* (typ *OLE_XPOS_PIXELS*).

9. Použití **typ parametru** a **název parametru** ovládací prvky, přidejte parametr s názvem *yCoord* (typ *OLE_YPOS_PIXELS*).

10. Klikněte na tlačítko **Dokončit**.

##  <a name="_core_classwizard_changes_for_custom_methods"></a> Přidejte metodu Průvodce změny pro vlastní metody

Když přidáte vlastní metodu, Průvodce přidáním metody provede některé změny záhlaví třídy ovládacího prvku (. H) a implementace (. Soubory CPP). Následující řádek je přidán do deklarace mapy odbavení v záhlaví třídy ovládacího prvku (. H) file:

[!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

Tento kód deklaruje obslužnou rutinu metody odeslání volá `PtInCircle`. Tuto funkci lze volat jeho uživatelem pomocí externího názvu `PtInCircle`.

Následující řádek je přidán do ovládacího prvku. Soubor IDL:

[!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

Tento řádek přiřadí `PtInCircle` metoda konkrétní identifikační číslo, metody pozici v seznamu Průvodce přidáním metody metody a vlastnosti. Vzhledem k tomu, že Průvodce přidáním metody se použil k přidání vlastní metodu, je zadání byl automaticky přidán do projektu. Soubor IDL.

Kromě toho na následujícím řádku umístěný v implementaci (. Mapa odbavení ovládacího prvku přidá soubor CPP) třídy ovládacího prvku:

[!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

DISP_FUNCTION – makro mapuje metodu `PtInCircle` funkci obslužná rutina ovládacího prvku, `PtInCircle`, deklaruje návratový typ jako **VARIANT_BOOL**a deklaruje dva parametry typu **VTS_XPOS_PIXELS** a **VTS_YPOSPIXELS** mají být předány `PtInCircle`.

A konečně, Průvodce přidáním metody přidá funkce se zakázaným inzerováním `CSampleCtrl::PtInCircle` k dolnímu okraji implementaci ovládacího prvku (. Soubor CPP). Pro `PtInCircle` fungovat tak, jak bylo uvedeno dříve, se musí být upraveny následujícím způsobem:

[!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[Ikony zobrazení třídy a prohlížeče objektů](/visualstudio/ide/class-view-and-object-browser-icons)
