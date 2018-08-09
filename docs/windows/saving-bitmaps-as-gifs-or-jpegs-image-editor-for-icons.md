---
title: Ukládání bitmap ve formátu GIF nebo JPEG (Editor obrázků pro ikony) | Dokumentace Microsoftu
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
ms.openlocfilehash: debb2b1e8435cc53ec82ab1f957710850d7b5de3
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010688"
---
# <a name="saving-bitmaps-as-gifs-or-jpegs-image-editor-for-icons"></a>Ukládání bitmap ve formátu GIF nebo JPEG (editor obrázků pro ikony)
Když vytvoříte rastrový obrázek, vytvoření image ve formátu rastrový obrázek (BMP). Image můžete, ale uložit jako ve formátu GIF nebo JPEG nebo v jiné formáty.  
  
> [!NOTE]
>  Tento proces se nevztahují na ikony a kurzory.  
  
### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Vytvoříte a uložíte rastrový obrázek GIF nebo JPEG  
  
1.  Z **souboru** nabídce zvolte **otevřít**, klikněte na **souboru**.  
  
2.  V **dialogové okno Nový soubor**, klikněte na tlačítko **Visual C++** složku, pak vyberte **rastrového obrázku (BMP)** v **šablony** pole a klikněte na tlačítko  **Otevřít**.  
  
     Rastrový obrázek se otevře v **Image** editoru.  
  
3.  Podle potřeby proveďte změny na nový rastrový obrázek.  
  
4.  Se stále otevřen v rastrového obrázku **Image** editoru klikněte na **Uložit *filename*.bmp jako** na **souboru** nabídky.  
  
5.  V **uložit soubor jako** dialogového okna zadejte název, kterému chcete udělit soubor a rozšíření, která označuje formát souboru, které chcete v **název_souboru** pole. Například *myfile.gif*.  
  
     > [!NOTE]
     > Musíte vytvořit nebo otevřít rastrového obrázku mimo projekt Pokud chcete uložit v jiném formátu. Pokud vytvoříte nebo jej otevřete v projektu **uložit jako** příkaz nebude k dispozici. Další informace najdete v tématu [zobrazování prostředků v prostředků skriptu souboru mimo of projekt (samostatný)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
6.  Klikněte na tlačítko **Uložit**.  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="see-also"></a>Viz také  
 [Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)