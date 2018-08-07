---
title: Změna velikosti obrázku (Editor obrázků pro ikony) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 41494e8b88f41c4c842e95e9f8a9f5da0247739f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605640"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>Změna velikosti obrázku (editor obrázků pro ikony)
Chování editoru obrázků při změně velikosti obrázku závisí na tom, jestli jste [vybrané](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) celého obrázku nebo jenom její část.  
  
 Pokud výběr obsahuje pouze část obrázku, editoru obrázků zmenšuje výběr odstraněním řádků nebo sloupců pixelů a vyplnění uvolněných oblastech pomocí aktuální barvu pozadí, nebo roztáhne výběr tak, že duplikujete řádky nebo sloupce v pixelech.  
  
 Pokud výběr zahrnuje celého obrázku, editoru obrázků buď zmenšuje a roztáhne bitovou kopii, nebo ořízne tak a rozšiřuje ji.  
  
 Pro změnu velikosti obrázku dvěma způsoby: úchyty pro změnu velikosti a [okno vlastností](/visualstudio/ide/reference/properties-window). Můžete přetažením úchytů změňte velikost všech nebo části obrázku. Jsou plné úchyty pro změnu velikosti, které můžete přetáhnout. Nelze přetáhnout popisovačů, které jsou prázdné. Okno vlastností pro změnu velikosti celého obrázku, vybrané části můžete použít.  
  
 ![Úchyty na rastrový obrázek](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")  
Úchyty pro změnu velikosti  
  
> [!NOTE]
>  Pokud máte dlaždici mřížky možnosti vybrané v [dialogové okno Nastavení mřížky](../windows/grid-settings-dialog-box-image-editor-for-icons.md), pak změnu velikosti při kolika rozehrávkách byli na další řádek mřížky dlaždice. Pokud je možnost mřížku obrazových bodů vybrán (výchozí nastavení), pouze změnu velikosti při kolika rozehrávkách byli na další bod k dispozici.  
  
-   [Změna velikosti celého obrázku](../windows/resizing-an-entire-image-image-editor-for-icons.md)  
  
-   [Oříznutí nebo rozšíření celého obrázku](cropping-or-extending-an-entire-image-image-editor-for-icons.md)  
  
-   [Zmenšení nebo roztažení celého obrázku](../windows/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)  
  
-   [Zmenšení nebo roztažení části obrázku](../windows/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)