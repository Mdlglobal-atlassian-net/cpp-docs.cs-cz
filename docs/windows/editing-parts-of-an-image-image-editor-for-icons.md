---
title: Úprava částí obrázku (Editor obrázků pro ikony) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
ms.assetid: ff4f5fef-71a4-4fd8-825e-049399fed391
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b33a591a2f38062b5eaf81b0f56ab73a36f4c90c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="editing-parts-of-an-image-image-editor-for-icons"></a>Úprava částí obrázku (editor obrázků pro ikony)
Můžete provádět operace standardní úpravy – vyjímání, kopírování, vymazání a přesouvání – na [výběr](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), zda se jedná celého obrázku nebo jenom část ho. Protože editor obrázků používá schránky systému Windows, můžou přenášet obrázky mezi editor obrázků a dalších aplikacích pro Windows.  
  
 Kromě toho můžete změnit velikost výběru, zda obsahuje celého obrázku nebo jenom část.  
  
### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Vyjmout aktuální výběr a přesunout ho do schránky.  
  
1.  Klikněte na tlačítko **Vyjmout** na **upravit** nabídky.  
  
### <a name="to-copy-the-selection"></a>Kopírovat výběr  
  
1.  Umístěte ukazatel uvnitř ohraničení výběru nebo kdekoli na něm s výjimkou úchyty.  
  
2.  Podržte stisknutou **CTRL** klíče a přetáhněte výběr do nového umístění. Oblasti původní výběru se nezmění.  
  
3.  Zkopírovat výběr do bitové kopie v jeho aktuálního umístění, klikněte na tlačítko mimo výběr kurzor.  
  
### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Chcete-li vložit obsah schránky do bitové kopie  
  
1.  Z **upravit** nabídce zvolte **vložení**.  
  
     V levém horním podokně se zobrazí obsah schránky, obklopená ohraničení výběru.  
  
2.  Umístěte ukazatel v rámci hranice výběru a přetáhněte bitovou kopii do požadovaného umístění na bitovou kopii.  
  
3.  Chcete-li ukotvení bitovou kopii v jeho novém umístění, klikněte na tlačítko mimo hranice výběru.  
  
### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Chcete-li odstranit aktuální výběr bez přesouvání do schránky.  
  
1.  Z **upravit** nabídce zvolte **odstranit**.  
  
     Původní oblasti výběru je vyplněn aktuální barvu pozadí.  
  
    > [!NOTE]
    >  Můžete získat přístup k vyjmutí, kopírování a vložení a odstranit příkazy kliknutím pravým tlačítkem v okně zobrazení zdrojů.  
  
### <a name="to-move-the-selection"></a>Výběr  
  
1.  Umístěte ukazatel uvnitř ohraničení výběru nebo kdekoli na něm s výjimkou úchyty.  
  
2.  Přetáhněte výběr do nového umístění.  
  
3.  Chcete-li ukotvení výběr do bitové kopie v jeho novém umístění, klikněte na tlačítko mimo hranice výběru.  
  
 Další informace o kreslení s výběrem najdete v tématu [vytvoření vlastního štětce](../windows/creating-a-custom-brush-image-editor-for-icons.md).  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Požadavky  
  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)

