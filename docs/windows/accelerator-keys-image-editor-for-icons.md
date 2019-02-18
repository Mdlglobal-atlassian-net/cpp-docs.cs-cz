---
title: Klávesy akcelerátoru (C++ Editor obrázků pro ikony)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
ms.openlocfilehash: 604f97edc8e4e49bad477d76e0e46334b8cf726b
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336534"
---
# <a name="accelerator-keys-c-image-editor-for-icons"></a>Klávesy akcelerátoru (C++ Editor obrázků pro ikony)

V následující tabulce jsou klávesy akcelerátoru pro editor příkazy bitové kopie, které jsou vázány na klíče ve výchozím nastavení. Chcete-li změnit klávesové zkratky, klikněte na tlačítko **možnosti** na **nástroje** nabídky a klikněte na tlačítko **klávesnice** v části **prostředí** složky. Další informace najdete v tématu [určení a přizpůsobení klávesových zkratek](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Dostupné možnosti v dialogových oknech, názvy a umístění příkazů, které vidíte, mohou lišit od informací uvedených v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Příkaz|klíče|Popis|
|-------------|----------|-----------------|
|Image.AirBrushTool|**Ctrl** + **A**|Kreslení pomocí rozprašovače se zvolenou velikostí a barvou.|
|Image.BrushTool|**Ctrl** + **B**|Kreslení pomocí štětce se vybraný tvar, velikostí a barvou.|
|Image.CopyAndOutlineSelection|**Ctrl** + **Shift** + **U**|Vytvoří kopii aktuálního výběru a zvýrazní ji. Je-li barvu pozadí je obsažen v aktuálním výběru, bude vyloučena v případě, že máte [transparentní](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) vybrané.|
|Image.DrawOpaque|**CTRL** + **J**|Změní aktuální výběr buď [neprůhledné nebo průhledné](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|Image.EllipseTool|**Ctrl** + **P**|Nakreslí elipsu s zvolenou šířku čáry a barvu.|
|Image.EraserTool|**Ctrl** + **Shift** + **I**|Vymaže část obrázku (aktuální barvou pozadí).|
|Image.FilledEllipseTool|**Ctrl** + **Shift** + **Alt** + **P**|Kreslení plné elipsy.|
|Image.FilledRectangleTool|**Ctrl** + **Shift** + **Alt** + **R**|Kreslení plného obdélníku.|
|Image.FilledRoundRectangleTool|**Ctrl** + **Shift** + **Alt** + **W**|Kreslení plného zaobleného obdélníku.|
|Image.FillTool|**CTRL** + **F**|Vyplní oblast.|
|Image.FlipHorizontal|**CTRL** + **H**|Převrátí obrázek nebo výběr vodorovně.|
|Image.FlipVertical|**SHIFT**+ **Alt** + **H**|Převrátí obrázek nebo výběr svisle.|
|Image.LargerBrush|**Ctrl** + **=**|Zvětší velikost štětce o jeden pixel v každém směru. Pro zmenšení velikosti štětce viz. Image.SmallerBrush v této tabulce.|
|Image.LineTool|**Ctrl** + **L**|Kreslení rovné čáry s vybraný tvar, velikostí a barvou.|
|Image.MagnificationTool|**Ctrl** + **M**|Aktivuje **Magnify** nástroj, který umožňuje zvětšit konkrétní část obrázku.|
|Image.Magnify|**CTRL** + **Shift** + **M**|Přepíná mezi aktuálním zvětšení a zvětšením 1:1.|
|Image.NewImageType|**Vložit**|Spustí [nový \<zařízení > obrázku dialogové okno](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md) pomocí které můžete vytvořit image pro typ jinou image.|
|Image.NextColor|**Ctrl** + **]**<br /><br /> - nebo -<br /><br /> **CTRL** + **šipka doprava**|Změní vykreslení barvy popředí na následující barvu z palety.|
|Image.NextRightColor|**Ctrl** + **Shift** + **]**<br /><br /> - nebo -<br /><br /> **SHIFT** + **Ctrl** + **šipka doprava**|Změní vykreslení barvy pozadí na následující barvu z palety.|
|Image.OutlinedEllipseTool|**SHIFT** + **Alt** + **P**|Kreslení plné elipsy s ohraničením.|
|Image.OutlinedRectangleTool|**SHIFT** + **Alt** + **R**|Kreslení plného obdélníku s ohraničením|
|Image.OutlinedRoundRectangleTool|**SHIFT** + **Alt** + **W**|Kreslení plného zaobleného obdélníku s ohraničením.|
|Image.PencilTool|**Ctrl** + **I**|Kreslení pomocí tužky jeden pixel.|
|Image.PreviousColor|**Ctrl** + **[**<br /><br /> - nebo -<br /><br /> **CTRL** + **šipka vlevo**|Změní vykreslení barvy popředí na předchozí barvu z palety.|
|Image.PreviousRightColor|**Ctrl** + **Shift** + **[**<br /><br /> - nebo -<br /><br /> **SHIFT** + **Ctrl** + **šipka vlevo**|Změní vykreslení barvy pozadí na předchozí barvu z palety.|
|Image.RectangleSelectionTool|**SHIFT** + **Alt** + **S**|Výběr obdélníkové části obrázku pro přesunutí, zkopírování nebo upravit.|
|Image.RectangleTool|ATL + R|Kreslení obdélníku s zvolenou šířku čáry a barvu.|
|Image.Rotate90Degrees|**CTRL** + **Shift** + **H**|Otočí obrázek nebo výběr o 90 stupňů.|
|Image.RoundedRectangleTool|**ALT** + **W**|Kreslení zaobleného obdélníku s zvolenou šířku čáry a barvu.|
|Image.ShowGrid|**Ctrl** + **Alt** + **S**|Přepíná mřížku pixelů (zaškrtne nebo zruší **mřížku obrazových bodů** možnost [dialogové okno Nastavení mřížky](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|
|Image.ShowTileGrid|**Ctrl** + **Shift** + **Alt** + **S**|Přepíná mřížku (zaškrtne nebo zruší **mřížka** možnost [dialogové okno Nastavení mřížky](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|
|Image.SmallBrush|**CTRL** + **.** (tečka)|Snižuje **štětce** velikost na jeden pixel. (Viz také Image.LargerBrush a Image.SmallerBrush v této tabulce.)|
|Image.SmallerBrush|**CTRL**  +  **-** (minus)|Zmenší velikost štětce o jeden pixel v každém směru. Zvětšení velikosti štětce znovu, viz. Image.LargerBrush v této tabulce.|
|Image.TextTool|**Ctrl** + **T**|Otevře [dialogové okno textový nástroj](../windows/text-tool-dialog-box-image-editor-for-icons.md).|
|Image.UseSelectionAsBrush|**Ctrl** + **U**|Kreslení štětcem pomocí aktuálního výběru.|
|Image.ZoomIn|**Ctrl** + **Shift** + **.** (tečka)<br /><br /> - nebo -<br /><br /> **CTRL** + **šipka nahoru**|Zvětšuje zvětšení aktuálního zobrazení.|
|Image.ZoomOut|**CTRL** + **,** (čárka)<br /><br /> - nebo -<br /><br /> **CTRL** + **šipka dolů**|Snižuje zvětšení aktuálního zobrazení.|

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také

[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)