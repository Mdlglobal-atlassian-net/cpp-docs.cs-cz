---
title: Převádění bitmap na panely nástrojů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor, converting bitmaps
- toolbars [C++], converting bitmaps
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e80bee7ef9bfe52abf63ac959475c5d8dbcf0ece
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="converting-bitmaps-to-toolbars"></a>Převádění bitmap na panely nástrojů
Převádění rastrový obrázek můžete vytvořit nový panel nástrojů. Na obrázku z bitmapy převede na pro obrázky tlačítka panelu nástrojů. Obvykle bitmapy obsahuje několik tlačítko bitových kopií na jednom rastrového obrázku, jednu bitovou kopií pro každé tlačítko. Bitové kopie může mít libovolnou velikost; Výchozí hodnota je 16 pixelů na šířku a výšku obrázku. Můžete zadat velikost tlačítko obrázků v [dialogové okno Nový prostředek panelu nástrojů](../windows/new-toolbar-resource-dialog-box.md) Pokud vyberete Editor panelu nástrojů z **Image** nabídky v editoru obrázků.  
  
### <a name="to-convert-bitmaps-to-a-toolbar"></a>Převod bitmap na panelu nástrojů  
  
1.  Otevřete existující prostředek rastrového obrázku v [editor obrázků](../windows/image-editor-for-icons.md). (Pokud bitovou mapu, již není v souboru .rc, klikněte pravým tlačítkem na soubor, vyberte **Import** z místní nabídky, přejděte na rastrový obrázek, který chcete přidat do souboru .rc a pak klikněte na **otevřete**.)  
  
2.  Z **Image** nabídce zvolte **Editor panelu nástrojů**.  
  
     [Dialogové okno Nový prostředek panelu nástrojů](../windows/new-toolbar-resource-dialog-box.md) se zobrazí. Můžete změnit šířku a výšku obrázků na ikonu tak, aby odpovídaly bitové mapy. Obrázek panelu nástrojů se následně zobrazí v editoru panelu nástrojů.  
  
3.  Chcete-li dokončit převod, změňte příkaz **ID** pomocí tlačítka [vlastnosti – okno](/visualstudio/ide/reference/properties-window). Zadejte nové **ID** nebo vyberte **ID** z rozevíracího seznamu.  
  
    > [!TIP]
    >  Okno vlastností obsahuje tlačítko připínáček v záhlaví. Kliknutím na toto tlačítko povolí nebo zakáže automatické skrýt okna. K rychlému procházení všechny vlastnosti tlačítka panelu nástrojů bez nutnosti znovu otevřete jednotlivé vlastnosti systému windows, vypněte automatické skrýt tak zůstane stojící okno vlastností.  
  
 Identifikátory příkazů tlačítek na panelu nástrojů nové můžete také změnit pomocí [vlastnosti – okno](/visualstudio/ide/reference/properties-window). Informace o nových nástrojů pro úpravy, najdete v části [vytváření, přesouvání a úpravy tlačítka panelu nástrojů](../windows/creating-moving-and-editing-toolbar-buttons.md).  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Požadavky  
  
 Knihovny MFC nebo knihovny ATL  
  
## <a name="see-also"></a>Viz také  
 [Vytváření nových panelů nástrojů](../windows/creating-new-toolbars.md)   
 [Editor panelu nástrojů](../windows/toolbar-editor.md)

