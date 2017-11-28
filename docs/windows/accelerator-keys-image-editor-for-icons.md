---
title: "Klávesy akcelerátoru (Editor obrázků pro ikony) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs: C++
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4eb2440602fefbbd2f42cbdde3f56745777e8e02
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="accelerator-keys-image-editor-for-icons"></a>Klávesy akcelerátoru (editor obrázků pro ikony)
V následující tabulce jsou klávesy akcelerátoru pro editor příkazy bitové kopie, které jsou vázány na klíče ve výchozím nastavení. Klávesy akcelerátoru změnit, klikněte na **možnosti** na **nástroje** nabídce a potom zvolte **klávesnice** pod **prostředí** složky. Další informace najdete v tématu [identifikuje a přizpůsobení klávesových zkratek](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).  
  
> [!NOTE]
>  K dispozici v dialogových oken, názvy a umístění příkazy nabídky, které vidíte, se může lišit od co je popsáno v nápovědě v závislosti na aktivním nastavení nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
|Příkaz|Klíče|Popis|  
|-------------|----------|-----------------|  
|Image.AirBrushTool|CTRL + A|Nakreslí rozprašovač pomocí vybrané velikosti a barvy.|  
|Image.BrushTool|CTRL + B|Nakreslí štětce pomocí vybraného obrazce, velikosti a barvy.|  
|Image.CopyAndOutlineSelection|CTRL + SHIFT + U|Vytvoří kopii aktuální výběr a popisuje ho. Pokud barvu pozadí je obsažena v aktuálním výběru, bude vyloučena Pokud máte [transparentní](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) vybrané.|  
|Image.DrawOpaque|CTRL + J|Aktuální výběr je buď [průhledná nebo neprůhledná](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|  
|Image.EllipseTool|CTRL + P|Nakreslí elipsy s vybranou tloušťkou čáry a barvy.|  
|Image.EraserTool|CTRL + SHIFT + I|Vymaže část bitové kopie (s aktuální barvu pozadí).|  
|Image.FilledEllipseTool|CTRL + SHIFT + ALT + P|Kreslení plné elipsy.|  
|Image.FilledRectangleTool|CTRL + SHIFT + ALT + R|Kreslení plného obdélníku.|  
|Image.FilledRoundRectangleTool|CTRL + SHIFT + ALT + W|Kreslení plného obdélníku zaokrouhlí.|  
|Image.FillTool|CTRL + F|Vyplní celé oblasti.|  
|Image.FlipHorizontal|CTRL + H|Převrátí bitovou kopii nebo výběr vodorovně.|  
|Image.FlipVertical|SHIFT + ALT + H|Převrátí bitovou kopii nebo výběr svisle.|  
|Image.LargerBrush|CTRL + =|Zvětšuje velikost štětce o jeden bod v každém směru. Chcete-li snížit velikost stopy, najdete v Image.SmallerBrush v této tabulce.|  
|Image.LineTool|CTRL + L|Nakreslí úsečku vybraného obrazce, velikosti a barvy.|  
|Image.MagnificationTool|CTRL + M|Aktivuje **Magnify** nástroj, který umožňuje zvětšit konkrétní části bitové kopie.|  
|Image.Magnify|CTRL + SHIFT + M|Přepne mezi aktuální zvětšení a zvětšení 1:1.|  
|Image.NewImageType|VLOŽENÍ|Spustí [nový \<zařízení > dialogové okno typ obrázku](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md) pomocí které můžete vytvořit bitovou kopii pro typ jinou bitovou kopii.|  
|Image.NextColor|CTRL +]<br /><br /> - nebo -<br /><br /> CTRL + ŠIPKA VPRAVO|Změny kreslení barvu popředí další palety barev.|  
|Image.NextRightColor|CTRL + SHIFT +]<br /><br /> - nebo -<br /><br /> SHIFT + CTRL + ŠIPKA DOPRAVA|Změní barvu pozadí kreslení na další palety barev.|  
|Image.OutlinedEllipseTool|SHIFT + ALT + P|Kreslení plné elipsy s úrovněmi.|  
|Image.OutlinedRectangleTool|SHIFT + ATL + R|Nakreslí plného obdélníku s osnovy|  
|Image.OutlinedRoundRectangleTool|SHIFT + ALT + W|Kreslení plného obdélníku zaokrouhlí s úrovněmi.|  
|Image.PencilTool|CTRL + I|Kreslení pomocí jednopixelové tužky.|  
|Image.PreviousColor|CTRL + [<br /><br /> - nebo -<br /><br /> CTRL + ŠIPKA VLEVO|Změny kreslení barvu popředí předchozí palety barev.|  
|Image.PreviousRightColor|CTRL + SHIFT + [<br /><br /> - nebo -<br /><br /> SHIFT + CTRL + ŠIPKA VLEVO|Změní barvu pozadí kreslení na předchozí palety barev.|  
|Image.RectangleSelectionTool|SHIFT + ALT + S|Vybere obdélníková část bitovou kopii přesunout, kopírovat nebo upravit.|  
|Image.RectangleTool|ATL + R|Kreslení obdélníku s vybranou tloušťkou čáry a barvy.|  
|Image.Rotate90Degrees|CTRL + SHIFT + H|Otočí obrázek nebo výběr 90 stupňů.|  
|Image.RoundedRectangleTool|ALT + W|Kreslení zaokrouhlí obdélníku s vybranou tloušťkou čáry a barvy.|  
|Image.ShowGrid|CTRL + ALT + S|Přepíná mřížky pixelů (vybere nebo vymaže **mřížky pixelů** možnost [dialogové okno Nastavení mřížky](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|  
|Image.ShowTileGrid|CTRL + SHIFT + ALT + S|Přepíná mřížky dlaždice (vybere nebo vymaže **dlaždice mřížky** možnost [dialogové okno Nastavení mřížky](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|  
|Image.SmallBrush|CTRL +. (tečka)|Snižuje **štětce** velikost o bod. (Viz také Image.LargerBrush a Image.SmallerBrush v této tabulce.)|  
|Image.SmallerBrush|CTRL + - (minus)|Snižuje velikost stopy o jeden bod v každém směru. Zvětšení velikosti štětce znovu, najdete v části Image.LargerBrush v této tabulce.|  
|Image.TextTool|CTRL + T|Otevře se [dialogové okno textový nástroj](../windows/text-tool-dialog-box-image-editor-for-icons.md).|  
|Image.UseSelectionAsBrush|CTRL + U|Kreslení pomocí aktuální výběr jako stopu.|  
|Image.ZoomIn|CTRL + SHIFT +. (tečka)<br /><br /> - nebo -<br /><br /> CTRL + ŠIPKA NAHORU|Zvyšuje zvětšení pro aktuální zobrazení.|  
|Image.ZoomOut|CTRL + (čárkou)<br /><br /> - nebo -<br /><br /> CTRL + ŠIPKA DOLŮ|Snižuje zvětšení aktuálního zobrazení.|  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
## <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)

