---
title: Klávesy akcelerátoru (C++ Editor obrázků pro ikony)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
ms.openlocfilehash: 062b860849d968e18657afb66b568a1bf6f2b6d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505102"
---
# <a name="accelerator-keys-c-image-editor-for-icons"></a>Klávesy akcelerátoru (C++ Editor obrázků pro ikony)

V následující tabulce jsou klávesy akcelerátoru pro editor příkazy bitové kopie, které jsou vázány na klíče ve výchozím nastavení. Chcete-li změnit klávesové zkratky, klikněte na tlačítko **možnosti** na **nástroje** nabídky a klikněte na tlačítko **klávesnice** v části **prostředí** složky. Další informace najdete v tématu [určení a přizpůsobení klávesových zkratek](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Dostupné možnosti v dialogových oknech, názvy a umístění příkazů, které vidíte, mohou lišit od informací uvedených v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Příkaz|klíče|Popis|
|-------------|----------|-----------------|
|Image.AirBrushTool|**CTRL** + **A**|Kreslení pomocí rozprašovače se zvolenou velikostí a barvou.|
|Image.BrushTool|**CTRL** + **B**|Kreslení pomocí štětce se vybraný tvar, velikostí a barvou.|
|Image.CopyAndOutlineSelection|**CTRL** + **Shift** + **U**|Vytvoří kopii aktuálního výběru a zvýrazní ji. Je-li barvu pozadí je obsažen v aktuálním výběru, bude vyloučena v případě, že máte [transparentní](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) vybrané.|
|Image.DrawOpaque|**CTRL** + **J**|Změní aktuální výběr buď [neprůhledné nebo průhledné](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|Image.EllipseTool|**CTRL** + **P**|Nakreslí elipsu s zvolenou šířku čáry a barvu.|
|Image.EraserTool|**CTRL** + **Shift** + **mi**|Vymaže část obrázku (aktuální barvou pozadí).|
|Image.FilledEllipseTool|**CTRL** + **Shift** + **Alt** + **P**|Kreslení plné elipsy.|
|Image.FilledRectangleTool|**CTRL** + **Shift** + **Alt** + **R**|Kreslení plného obdélníku.|
|Image.FilledRoundRectangleTool|**CTRL** + **Shift** + **Alt** + **W**|Kreslení plného zaobleného obdélníku.|
|Image.FillTool|**CTRL** + **F**|Vyplní oblast.|
|Image.FlipHorizontal|**CTRL** + **H**|Převrátí obrázek nebo výběr vodorovně.|
|Image.FlipVertical|**SHIFT**+ **Alt** + **H**|Převrátí obrázek nebo výběr svisle.|
|Image.LargerBrush|**CTRL** + **=**|Zvětší velikost štětce o jeden pixel v každém směru. Pro zmenšení velikosti štětce viz. Image.SmallerBrush v této tabulce.|
|Image.LineTool|**CTRL** + **L**|Kreslení rovné čáry s vybraný tvar, velikostí a barvou.|
|Image.MagnificationTool|**CTRL** + **M**|Aktivuje **Magnify** nástroj, který umožňuje zvětšit konkrétní část obrázku.|
|Image.Magnify|**CTRL** + **Shift** + **M**|Přepíná mezi aktuálním zvětšení a zvětšením 1:1.|
|Image.NewImageType|**Vložit**|Spustí [nový \<zařízení > obrázku dialogové okno](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md) pomocí které můžete vytvořit image pro typ jinou image.|
|Image.NextColor|**CTRL** + **]**<br /><br /> - nebo -<br /><br /> **CTRL** + **šipka doprava**|Změní vykreslení barvy popředí na následující barvu z palety.|
|Image.NextRightColor|**CTRL** + **Shift** + **]**<br /><br /> - nebo -<br /><br /> **SHIFT** + **Ctrl** + **šipka doprava**|Změní vykreslení barvy pozadí na následující barvu z palety.|
|Image.OutlinedEllipseTool|**SHIFT** + **Alt** + **P**|Kreslení plné elipsy s ohraničením.|
|Image.OutlinedRectangleTool|**SHIFT** + **Alt** + **R**|Kreslení plného obdélníku s ohraničením|
|Image.OutlinedRoundRectangleTool|**SHIFT** + **Alt** + **W**|Kreslení plného zaobleného obdélníku s ohraničením.|
|Image.PencilTool|**CTRL** + **mi**|Kreslení pomocí tužky jeden pixel.|
|Image.PreviousColor|**CTRL** + **[**<br /><br /> - nebo -<br /><br /> **CTRL** + **šipka vlevo**|Změní vykreslení barvy popředí na předchozí barvu z palety.|
|Image.PreviousRightColor|**CTRL** + **Shift** + **[**<br /><br /> - nebo -<br /><br /> **SHIFT** + **Ctrl** + **šipka vlevo**|Změní vykreslení barvy pozadí na předchozí barvu z palety.|
|Image.RectangleSelectionTool|**SHIFT** + **Alt** + **S**|Výběr obdélníkové části obrázku pro přesunutí, zkopírování nebo upravit.|
|Image.RectangleTool|ATL – + R|Kreslení obdélníku s zvolenou šířku čáry a barvu.|
|Image.Rotate90Degrees|**CTRL** + **Shift** + **H**|Otočí obrázek nebo výběr o 90 stupňů.|
|Image.RoundedRectangleTool|**ALT** + **W**|Kreslení zaobleného obdélníku s zvolenou šířku čáry a barvu.|
|Image.ShowGrid|**CTRL** + **Alt** + **S**|Přepíná mřížku pixelů (zaškrtne nebo zruší **mřížku obrazových bodů** možnost [dialogové okno Nastavení mřížky](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|
|Image.ShowTileGrid|**CTRL** + **Shift** + **Alt** + **S**|Přepíná mřížku (zaškrtne nebo zruší **mřížka** možnost [dialogové okno Nastavení mřížky](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|
|Image.SmallBrush|**CTRL** + **.** (tečka)|Snižuje **štětce** velikost na jeden pixel. (Viz také Image.LargerBrush a Image.SmallerBrush v této tabulce.)|
|Image.SmallerBrush|**CTRL**  +  **-** (minus)|Zmenší velikost štětce o jeden pixel v každém směru. Zvětšení velikosti štětce znovu, viz. Image.LargerBrush v této tabulce.|
|Image.TextTool|**Ctrl** + **T**|Otevře [dialogové okno textový nástroj](../windows/text-tool-dialog-box-image-editor-for-icons.md).|
|Image.UseSelectionAsBrush|**CTRL** + **U**|Kreslení štětcem pomocí aktuálního výběru.|
|Image.ZoomIn|**CTRL** + **Shift** + **.** (tečka)<br /><br /> - nebo -<br /><br /> **CTRL** + **šipka nahoru**|Zvětšuje zvětšení aktuálního zobrazení.|
|Image.ZoomOut|**CTRL** + **,** (čárka)<br /><br /> - nebo -<br /><br /> **CTRL** + **šipka dolů**|Snižuje zvětšení aktuálního zobrazení.|

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)