---
title: Změna velikosti ovládacích prvků
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.combo
helpviewer_keywords:
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
- Make Same Size command
- combo boxes, sizing
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
ms.openlocfilehash: a6381dcf1aeb9f73ac3b656229d9332df2a6a519
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742710"
---
# <a name="sizing-controls"></a>Změna velikosti ovládacích prvků

Použijte úchyty pro změnu velikosti ovládacího prvku. Pokud je ukazatel myši umístěn na úchyt pro změnu velikosti, změní tvar, který má označení směry, ve kterých můžete změnit velikost ovládacího prvku. Aktivní úchyty jsou pořádné; Pokud je dutý úchyt pro změnu velikosti, ovládací prvek nelze změnit velikost podél osy.

Můžete také změnit velikost ovládacího prvku pomocí přichycení vodítka a okraje ovládacího prvku, nebo přesunutím jeden přichycené zobrazení ovládacího prvku a Průvodce mimo jiné.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-size-an-individual-control"></a>Pro nastavení velikosti jednotlivé ovládací prvky

1. Vyberte ovládací prvek.

1. Přetažením úchytů změňte velikost ovládacího prvku:

   - Úchyty pro změnu velikosti na začátku a konce změnit velikost vodorovně nebo svisle.

   - Úchyty pro změnu velikosti v rozích změnit šířku a výšku.

   > [!TIP]
   > Můžete změnit velikost jednotky jeden dialogového okna ovládacího prvku (DLU) současně současným **Shift** klíče a pomocí **šipka vpravo** a **šipka dolů** klíče.

## <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>Chcete-li automaticky velikost ovládacího prvku podle textu v rámci něj

Zvolte **velikost, aby se obsah** z **formátu** nabídky.

\- nebo –

Klikněte pravým tlačítkem na ovládací prvek a vyberte **velikost obsahu** z místní nabídky.

## <a name="to-make-controls-the-same-width-height-or-size"></a>Aby se řídí stejnou šířku, výšku ani velikost

Změnit velikost skupiny ovládacích prvků na základě velikosti dominantního ovládacího prvku.

1. [Vyberte ovládací prvky](../windows/selecting-multiple-controls.md) chcete změnit velikost.

   Ovládací prvek nejprve v řadě je dominantního ovládacího prvku. Konečné velikosti ovládacích prvků ve skupině závisí na velikosti dominantního ovládacího prvku. Další informace o výběru dominantního ovládacího prvku, naleznete v tématu [určení dominantního ovládacího prvku](../windows/specifying-the-dominant-control.md).

1. Z **formátu** nabídce zvolte **nastavit stejnou velikost**, pak vyberte jednu z následujících příkazů:

   - **Obojí**

   - **Výška**

   - **Šířka**

## <a name="to-set-the-size-of-the-combo-box-and-its-drop-down-list"></a>K nastavení velikosti pole se seznamem pole a jeho rozevíracího seznamu

Při přidání do dialogových oken, můžete měnit velikost pole se seznamem. Můžete také určit velikost pole rozevíracího seznamu. Další informace najdete v tématu [přidání hodnot do ovládacího prvku pole se seznamem](../windows/adding-values-to-a-combo-box-control.md).

### <a name="to-size-a-combo-box"></a>Pro nastavení velikosti pole se seznamem

1. Vyberte ovládací prvek pole se seznamem ve vašem dialogovém okně.

   Na začátku jsou aktivní pouze vpravo a vlevo úchyty.

1. Pomocí úchytů nastavte šířku pole se seznamem.

Můžete také nastavit velikost svislé rozbalovaná část pole se seznamem.

### <a name="to-set-the-size-of-the-combo-box-drop-down-list"></a>Nastavení velikosti pole se seznamem pole rozevíracího seznamu

1. Vyberte tlačítko se šipkou rozevíracího seznamu na pravé straně pole se seznamem.

   ![Šipka na pole se seznamem v projektu knihovny MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Přehled ovládacího prvku změn zobrazíte velikost pole se seznamem s rozevíracího seznamu oblastí extended.

1. Chcete-li změnit počáteční velikost oblasti rozevíracího seznamu použijte dolní úchyt pro změnu velikosti.

   ![Pole se seznamem&#45;nastavení velikosti pole v projektu knihovny MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Vyberte šipku rozevíracího seznamu zavřete rozevírací část pole se seznamem.

## <a name="to-set-the-width-of-a-horizontal-scroll-bar-and-make-it-appear"></a>Nastavení šířky vodorovného posuvníku a usnadnit zobrazí

Když přidáte seznam s vodorovný posuvník do dialogového okna pomocí tříd knihovny MFC, posuvník nezobrazí automaticky ve vaší aplikaci.

Nastavte maximální šířku prvku nejširší voláním [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) ve vašem kódu.

   Bez této sady hodnot posuvník nezobrazí, i když jsou položky v seznamu širší než pole.
> [!NOTE]
> Vodorovný posuvník vyžaduje knihovny MFC.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
