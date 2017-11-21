---
title: "Vytvoření obrázku zařízení (Editor obrázků pro ikony) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.icon
dev_langs: C++
helpviewer_keywords:
- cursors [C++], creating
- icons [C++], creating
- display devices
- display devices, creating image
- images [C++], creating for display devices
- icons [C++], inserting
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8a4f71b2877eaaa7af125918c7fe2b71bb031d39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>Vytvoření obrázku zařízení (editor obrázků pro ikony)
Když vytvoříte nový ikony nebo kurzoru prostředek, bitovou kopii, editor nejprve vytvoří bitovou kopii v konkrétním stylu (32 x 32, 16 barvy u ikon a 32 × 32, černobílý tisk pro kurzory). Můžete přidat Image do počáteční ikony nebo kurzoru v různých velikostech a styly a upravit každé další bitové kopie, podle potřeby pro zařízení s jiným zobrazením. Můžete taky upravit bitovou kopii pomocí operace vyjímání a vkládání z existujícího typu image nebo rastrového obrázku vytvořeného v grafickém programu.  
  
 Když otevřete prostředek ikony nebo kurzoru [editor obrázků](../windows/image-editor-for-icons.md), bitovou kopii většina úzce odpovídající aktuální zobrazovací zařízení je otevřen ve výchozím nastavení.  
  
### <a name="to-create-a-new-icon-or-cursor"></a>Chcete-li vytvořit nové ikony nebo kurzoru  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na váš soubor .rc, a potom vyberte **vložit prostředků** z místní nabídky. (Pokud již máte existující zdroj bitové kopie v souboru .rc, jako je například kurzoru, můžete můžete jednoduše klikněte pravým tlačítkem myši **kurzor** složky a vyberte **vložení kurzoru** z místní nabídky.)  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  V [dialogové okno Vložit prostředek](../windows/add-resource-dialog-box.md), vyberte **ikonu** nebo **kurzor** a klikněte na tlačítko **nový**. U ikon vytvoří prostředek s ikonou s 32 × 32, ikona 16 barev. Kurzory, 32 × 32, Černobílý bitová kopie (2-color) vytvořena.  
  
     Pokud znaménko plus (**+**) se zobrazí u typu prostředku bitové kopie v **vložit prostředků** dialogové okno, znamená to, že nástrojů šablony jsou k dispozici. Kliknutím na znaménko plus rozbalte seznam šablon, vyberte šablonu a klikněte na tlačítko **nový**.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 **Požadavky**  
  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Ikony a kurzory: prostředky obrázků pro zařízení s displejem](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Ikony a kurzory: prostředky obrázků pro zařízení s displejem](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)
