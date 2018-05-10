---
title: Ukládání bitmap ve formátu GIF nebo JPEG (Editor obrázků pro ikony) | Microsoft Docs
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
- .gif files, saving bitmaps as
- jpg files, saving bitmaps as
- jpeg files, saving bitmaps as
- .jpg files, saving bitmaps as
- Image editor [C++], converting image formats
- gif files, saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files, saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 115df69f-10fb-4e6f-906b-853c1e4a54af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aed35f50e8cb874cea833439150b717034244b95
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="saving-bitmaps-as-gifs-or-jpegs-image-editor-for-icons"></a>Ukládání bitmap ve formátu GIF nebo JPEG (editor obrázků pro ikony)
Když vytvoříte rastrový obrázek, vytvoří se ve formátu rastrový obrázek (BMP) bitovou kopii. Můžete však uložit obrázek jako GIF nebo JPEG nebo v jiné grafické formáty.  
  
> [!NOTE]
>  Tento proces se nevztahuje na ikony a kurzory.  
  
### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Vytvoření a uložení rastrový obrázek jako GIF nebo JPEG  
  
1.  Z **soubor** nabídce zvolte **otevřete**, pak klikněte na tlačítko **soubor**.  
  
2.  V **dialogové okno Nový soubor**, klikněte na tlačítko **Visual C++** složku, pak vyberte **souboru rastrový obrázek (BMP)** v **šablony** pole a klikněte na tlačítko  **Otevřete**.  
  
     Bitmapy se otevře v **Image** editor.  
  
3.  Podle potřeby proveďte změny nové bitmapy.  
  
4.  Se stále otevřen v rastrového obrázku **bitové kopie** editoru klikněte na **Uložit *filename*.bmp jako** na **souboru** nabídky.  
  
5.  V **uložit soubor jako** dialogovém okně zadejte název, který chcete poskytnout soubor a rozšíření, která označuje formát souboru, které mají být v **název souboru** pole. Například myfile.gif.  
  
     **Poznámka:** musíte vytvořit nebo otevřít rastrového obrázku mimo projekt a uložte ho jako jiný formát souboru. Pokud vytvoříte nebo ho otevřete v projektu, **uložit jako** příkaz nebude k dispozici. Další informace najdete v tématu [zobrazení prostředků v prostředků skriptu souboru mimo of projekt (samostatný)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
6.  Klikněte na tlačítko **Uložit**.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="see-also"></a>Viz také  
 [Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)

