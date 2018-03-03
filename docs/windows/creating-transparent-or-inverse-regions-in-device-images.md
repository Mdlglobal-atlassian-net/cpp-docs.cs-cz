---
title: "Vytvoření průhledných nebo obrácených oblastí v obrázcích zařízení (Editor obrázků pro ikony) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], screen regions
- inverse colors, device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices, transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects, transparent images
- icons [C++], screen regions
ms.assetid: a994954b-b039-4391-a535-58d1fa10fc3b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f416b31200352fc849fb2d1c7a43f9759da47d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-transparent-or-inverse-regions-in-device-images-image-editor-for-icons"></a>Vytvoření průhledných nebo obrácených oblastí v obrázcích zařízení (editor obrázků pro ikony)
V [editor obrázků](../windows/image-editor-for-icons.md), má atribut transparentní počáteční obrázek ikony nebo kurzoru. I když jsou obdélníková ikonu a kurzor bitové kopie, mnoho se nezobrazí, protože částí obrázku jsou transparentní; základní bitovou kopii na obrazovce zobrazuje pomocí ikony nebo kurzoru. Při přetažení ikonu částí obrázku se mohou objevit v obráceným barev. Vytvoříte tento účinek nastavení barvy obrazovky a inverzní barvy v [barvy – okno](../windows/colors-window-image-editor-for-icons.md).  
  
 Barvy obrazovky a inverzní použijete ikony a kurzory buď utvářejí a barvu bitovou kopii odvozené nebo určit inverzní oblasti. Barvy označují částí obrázku s těmito atributy. Barvy, které představují atributy barvy obrazovky a inverzní barvy k úpravám, můžete změnit. Tyto změny neovlivňují vzhled ikony nebo kurzoru ve vaší aplikaci.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-transparent-or-inverse-regions"></a>Vytvoření průhledných nebo obrácených oblastí  
  
1.  V **barvy** okně klikněte na tlačítko **barvy obrazovky** selektor nebo **inverzní barvy** selektor.  
  
2.  Použijte obrazovky nebo inverzní barvy na používání nástroje kreslení image. Další informace o nástrojů pro kreslení najdete v tématu [používání nástroje kreslení](using-a-drawing-tool-image-editor-for-icons.md).  
  
### <a name="to-change-the-screen-or-inverse-color"></a>Změna obrazovky nebo inverzní barvy  
  
1.  Vyberte buď **barvy obrazovky** selektor nebo **inverzní barvy** selektor.  
  
2.  Vyberte barvu ze **barvy** palety v **barvy** okno.  
  
     Doplňkové barvy je automaticky určeno pro jiné selektor.  
  
    > [!TIP]
    >  Pokud dvakrát kliknete výběr barvy obrazovky nebo inverzní barvy [dialogové okno Výběr vlastních barev](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) se zobrazí.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Požadavky  
  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Ikony a kurzory: prostředky obrázků pro zařízení s displejem](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

