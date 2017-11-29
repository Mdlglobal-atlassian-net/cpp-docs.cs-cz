---
title: "Změna velikosti obrázku (Editor obrázků pro ikony) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.image.editing
dev_langs: C++
helpviewer_keywords:
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6c6e8d5e4704f9dda9399d67de5b3d0f93d283a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="resizing-an-image-image-editor-for-icons"></a>Změna velikosti obrázku (editor obrázků pro ikony)
Chování editor obrázků při změně velikosti obrázku závisí na tom, jestli jste [vybrané](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) celého obrázku nebo jenom součást.  
  
 Pokud výběr obsahuje pouze část obrázku, editor obrázků zúží výběr odstraněním řádků nebo sloupce pixelů a naplnění vacated oblasti s aktuální barvu pozadí nebo roztahovány výběr duplikováním řádky nebo sloupce pixelů.  
  
 Pokud výběr zahrnuje celého obrázku, editor obrázků buď zmenšuje roztahovány bitovou kopii, nebo ořízne a rozšiřuje ji.  
  
 Pro změnu velikosti obrázku dvěma způsoby: úchyty a [vlastnosti – okno](/visualstudio/ide/reference/properties-window). Můžete přetáhnout úchyty změnit velikost všech nebo části obrázku. Nastavení velikosti obslužných rutin, které můžete přetáhnout jsou pevné. Nelze přetáhnout obslužných rutin, které jsou prázdné. Okno vlastností ke změně velikosti celého obrázku, není vybraná část můžete použít.  
  
 ![Změna velikosti popisovače na rastrový obrázek](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")  
Změna velikosti obslužných rutin  
  
> [!NOTE]
>  Pokud máte dlaždici mřížky možnosti vybrané v [dialogové okno Nastavení mřížky](../windows/grid-settings-dialog-box-image-editor-for-icons.md), pak změna velikosti rozehrávkách byli na další řádek mřížky dlaždice. Pokud je možnost mřížky pixelů vybrán (výchozí nastavení), pouze změna velikosti rozehrávkách byli o další bod k dispozici.  
  
-   [Změna velikosti celého obrázku](../windows/resizing-an-entire-image-image-editor-for-icons.md)  
  
-   [Oříznutí nebo rozšíření celého obrázku](cropping-or-extending-an-entire-image-image-editor-for-icons.md)  
  
-   [Zmenšení nebo roztažení celého obrázku](../windows/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)  
  
-   [Zmenšení nebo roztažení části obrázku](../windows/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
## <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)
