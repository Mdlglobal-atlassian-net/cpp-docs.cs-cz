---
title: Vytvoření ikony nebo jiného obrázku (Editor obrázků pro ikony) | Dokumentace Microsoftu
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
ms.openlocfilehash: b708d701bee433857f8d5f8379d74b92375340de
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651918"
---
# <a name="creating-an-icon-or-other-image-image-editor-for-icons"></a>Vytvoření ikony nebo jiného obrázku (editor obrázků pro ikony)
Můžete vytvořit novou bitovou kopii (rastrový obrázek, ikona, kurzoru nebo panelu nástrojů) a potom použít editor obrázků přizpůsobit její vzhled. Můžete také vytvořit nový rastrový obrázek vzorované po [šablony](../windows/how-to-use-resource-templates.md).  
  
### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>Chcete-li přidat nový prostředek obrázku do nespravované projektu C++  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc a pak zvolte **vložit prostředků** z místní nabídky. (Pokud už máte existující prostředek obrázku v souboru .rc, jako je například kurzor, můžete můžete jednoduše kliknout pravým tlačítkem **kurzor** a pak zvolte položku **vložení kurzoru** z místní nabídky.)  
  
    > [!NOTE]
    > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  V [vložit prostředek – dialogové okno](../windows/add-resource-dialog-box.md), vyberte typ, který chcete vytvořit prostředek obrázku (**rastrový obrázek**, například) klikněte na **nový**.  
  
     Pokud symbol plus (**+**) se zobrazí u typu prostředku bitové kopie v **vložit prostředků** dialogové okno, znamená to, že šablony nástrojů jsou k dispozici. Klikněte na znaménko plus rozbalit seznam šablon, vyberte šablonu a klikněte na **nový**.  
  
### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>Chcete-li přidat nový prostředek obrázku do projektu v .NET programovací jazyk  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na složku projektu (například `WindowsApplication1`).  
  
2.  V místní nabídce klikněte na tlačítko **přidat**, klikněte na tlačítko **přidat novou položku**.  
  
3.  V **kategorie** podokně rozbalte **místní položky projektu** složky, klikněte na tlačítko **prostředky**.  
  
4.  V **šablony** podokně, vyberte typ prostředku, který chcete přidat do projektu.  
  
     Prostředek se přidá do vašeho projektu v **Průzkumníka řešení** a prostředek se otevře [editor obrázků](../windows/image-editor-for-icons.md). Všechny nástroje, které jsou k dispozici v editoru obrázků můžete nyní upravovat bitové kopie. Další informace o přidávání bitové kopie do spravovaných projektů naleznete v tématu [načítání obrázku v době návrhu](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).  
  
    > [!NOTE]
    >  Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků. Další informace najdete v tématu [Creating Resource Files](/dotnet/framework/resources/creating-resource-files-for-desktop-apps) v *rozhraní .NET Framework Developer's Guide*.  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Ikony a kurzory: prostředky obrázků pro zobrazovací zařízení](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [Převádění bitmap na panely nástrojů](../windows/converting-bitmaps-to-toolbars.md)   
 [Vytváření nových panelů nástrojů](../windows/creating-new-toolbars.md)   
 [Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)