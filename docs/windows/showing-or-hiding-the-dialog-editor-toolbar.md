---
title: Zobrazení nebo skrytí panelu nástrojů editoru dialogového okna | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog editor, showing or hiding toolbar
ms.assetid: 93c255e1-90eb-48b6-8602-450acda75bed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f1aa9e84e1f03f0299d25ec43b91c93531179ab6
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599409"
---
# <a name="showing-or-hiding-the-dialog-editor-toolbar"></a>Zobrazení nebo skrytí panelu nástrojů editoru dialogového okna

Když otevřete **dialogové okno** editoru **editoru dialogového okna** nástrojů se automaticky zobrazí v horní části vašeho řešení.

### <a name="dialog-editor-toolbar"></a>Panel nástrojů editoru dialogového okna

|Ikona|Význam|Ikona|Význam|
|----------|-------------|----------|-------------|
|![Tlačítko Testovat Dialog](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Testovací dialogové okno|![Místo přes tlačítko](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Mezi|
|![Zarovnat doleva tlačítko](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Zarovnat doleva|![Tlačítko místo dolů](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Dolů|
|![Zarovnat práva tlačítko](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Zarovnat doprava|![Ujistěte se stejnou šířku tlačítka](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Nastavit stejnou šířku|
|![Zarovnat horní tlačítko](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Zarovnat nahoru|![Ujistěte se stejnou výškou tlačítko](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Stejná výška|
|![Zarovnat DNA tlačítko](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Zarovnat dolů|![Ujistěte se stejnou velikostí tlačítko](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Nastavit stejnou velikost|
|![Tlačítko svisle Center](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Svisle|![Přepínací tlačítko mřížky](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Přepnout mřížku|
|![Vodorovná tlačítka Center](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Vodorovná|![Tlačítko průvodce přepínací tlačítko](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Průvodce přepínací tlačítko|

**Editoru dialogového okna** nástrojů obsahuje tlačítka pro uspořádání rozložení ovládacích prvků v dialogovém okně třeba velikost a zarovnání. **Editor dialogových oken** tlačítka na panelu nástrojů odpovídají příkazy na **formátu** nabídky. Podrobnosti najdete v tématu [klávesy akcelerátoru pro Editor dialogového okna](../windows/accelerator-keys-for-the-dialog-editor.md).

Pokud pracujete s **dialogové okno** editoru můžete přepínat zobrazení **editoru dialogového okna** nástrojů tak, že ho vyberete ze seznamu dostupných panelů nástrojů a oken.

### <a name="to-show-or-hide-the-dialog-editor-toolbar"></a>Zobrazení nebo skrytí panelu nástrojů editoru dialogového okna

1. Na **zobrazení** klikněte na nabídku **panely nástrojů** klikněte na tlačítko **editoru dialogového okna** z podnabídky.

   > [!NOTE]
   > **Editoru dialogového okna** nástrojů je ve výchozím nastavení zobrazí, když otevřete zdroj dialogového okna v editoru dialogového okna; nicméně, pokud explicitně Zavřít panel nástrojů, budete muset ho vyvolat při příštím otevření zdroj dialogového okna.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Uspořádání ovládacích prvků v dialogových oknech](../windows/arrangement-of-controls-on-dialog-boxes.md)  
[Postupy: Vytvoření prostředku](../windows/how-to-create-a-resource.md)  
[Soubory prostředků](../windows/resource-files-visual-studio.md)  
[Editor dialogových oken](../windows/dialog-editor.md)