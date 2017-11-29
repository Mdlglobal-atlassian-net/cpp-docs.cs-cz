---
title: "Vytvoření 256 barvami ikony nebo kurzoru (Editor obrázků pro ikony) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- 256-color palette
- cursors, color
- colors, icons
- colors, cursors
- icons, color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 12baf092d432aff4ac16d00f1877128eef629e14
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-256-color-icon-or-cursor-image-editor-for-icons"></a>Vytvoření ikony nebo kurzoru s 256 barvami (editor obrázků pro ikony)
Editor obrázků, ikony a kurzory může být použití velikostí velké (64 x 64) s 256 barvami palety lze vybírat. Po vytvoření prostředku, je vybrán zařízení styl bitové kopie.  
  
### <a name="to-create-a-256-color-icon-or-cursor"></a>Chcete-li vytvořit 256 barvami ikony nebo kurzoru s  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na váš soubor .rc, a potom vyberte **vložit prostředků** z místní nabídky. (Pokud již máte existující zdroj bitové kopie v souboru .rc, jako je například kurzoru, můžete můžete jednoduše klikněte pravým tlačítkem myši **kurzor** složky a vyberte **vložení kurzoru** z místní nabídky.)  
  
     **Poznámka:** Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  V [dialogové okno Vložit prostředek](../windows/add-resource-dialog-box.md), vyberte **ikonu** nebo **kurzor** a klikněte na tlačítko **nový**.  
  
3.  Na **Image** nabídky, klikněte na tlačítko **novou bitovou kopii zařízení**.  
  
4.  Vyberte požadovaný styl 256 barvami image.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 **Požadavky**  
  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Používání palety 256 barvami](../windows/using-the-256-color-palette-image-editor-for-icons.md)   
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Ikony a kurzory: prostředky obrázků pro zařízení s displejem](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)
