---
title: Vytvoření ikony nebo jiného obrázku (Editor obrázků pro ikony) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resource toolbars
- resources [Visual Studio], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2138e32b18f2e15de027e3cc04fb1bd7ee46ecd5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="creating-an-icon-or-other-image-image-editor-for-icons"></a>Vytvoření ikony nebo jiného obrázku (editor obrázků pro ikony)
Můžete vytvořit novou bitovou kopii (rastrového obrázku, ikona, kurzor nebo panelu nástrojů) a pak pomocí editoru obrázků přizpůsobit její vzhled. Můžete také vytvořit nové bitmapy vzorované po [šablony](../windows/how-to-use-resource-templates.md).  
  
### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>Chcete-li přidat nový prostředek bitové kopie do nespravovaných projektu C++  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na váš soubor .rc, a potom vyberte **vložit prostředků** z místní nabídky. (Pokud již máte existující zdroj bitové kopie v souboru .rc, jako je například kurzoru, můžete můžete jednoduše klikněte pravým tlačítkem myši **kurzor** složky a vyberte **vložení kurzoru** z místní nabídky.)  
  
    > [!NOTE]
    >  **Poznámka:** Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  V [dialogové okno Vložit prostředek](../windows/add-resource-dialog-box.md), vyberte typ prostředku bitové kopie, které chcete vytvořit (**rastrový obrázek**, například) klikněte **nový**.  
  
     Pokud znaménko plus (**+**) se zobrazí u typu prostředku bitové kopie v **vložit prostředků** dialogové okno, znamená to, že nástrojů šablony jsou k dispozici. Kliknutím na znaménko plus rozbalte seznam šablon, vyberte šablonu a klikněte na tlačítko **nový**.  
  
### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>Chcete-li přidat nový prostředek bitové kopie na projekt v .NET programovací jazyk  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na složku projekt (například **WindowsApplication1**).  
  
2.  V místní nabídce klikněte na **přidat**, zvolte **přidat novou položku**.  
  
3.  V **kategorie** podokně rozbalte **místní položky projektu** složku, pak zvolte **prostředky**.  
  
4.  V **šablony** podokně, vyberte typ prostředku, který chcete přidat do projektu.  
  
     Prostředek se přidá do projektu v Průzkumníku řešení a prostředek se otevře v [editor obrázků](../windows/image-editor-for-icons.md). Teď můžete všechny nástroje, které jsou k dispozici v editoru obrázků k úpravě bitové kopie. Další informace o přidávání obrázků na spravovaný projekt, najdete v části [načítání obrázku v době návrhu](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).  
  
    > [!NOTE]
    >  Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků. Další informace najdete v tématu [vytváření souborů prostředků](/dotnet/framework/resources/creating-resource-files-for-desktop-apps) v *rozhraní .NET Framework – příručka vývojáře*.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Požadavky  
  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Ikony a kurzory: prostředky obrázků pro zařízení s displejem](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [Převádění bitmap na panely nástrojů](../windows/converting-bitmaps-to-toolbars.md)   
 [Vytváření nových panelů nástrojů](../windows/creating-new-toolbars.md)   
 [Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)

