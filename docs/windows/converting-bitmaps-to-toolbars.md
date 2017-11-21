---
title: "Převádění bitmap na panely nástrojů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor, converting bitmaps
- toolbars [C++], converting bitmaps
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 43eda0c6bd875b9fd82ee97d346e3f5d89584795
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 Požadavky  
  
 Knihovny MFC nebo knihovny ATL  
  
## <a name="see-also"></a>Viz také  
 [Vytváření nových panelů nástrojů](../windows/creating-new-toolbars.md)   
 [Editor panelu nástrojů](../windows/toolbar-editor.md)

