---
title: Přidání hodnot do ovládacího prvku pole se seznamem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.combo
dev_langs:
- C++
helpviewer_keywords:
- combo boxes [C++], Data property
- controls [Visual Studio], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- controls [C++], testing values in combo boxes
- Data property
- combo boxes [C++], testing values
ms.assetid: 22a78f98-fada-48b3-90d8-7fa0d8e4de51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3760da2fad7596938acf881cd36af099ad1253cf
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643793"
---
# <a name="adding-values-to-a-combo-box-control"></a>Přidání hodnot do ovládacího prvku pole se seznamem
Můžete přidat hodnoty do ovládacího prvku pole se seznamem za předpokladu, že máte **dialogové okno** editoru otevřít.  
  
> [!TIP]
>  Je vhodné přidat všechny hodnoty do pole se seznamem *před* velikost pole **dialogové okno** editoru, nebo může zkrátit text, který by se měla zobrazit v ovládacím prvku pole se seznamem.  
  
### <a name="to-enter-values-into-a-combo-box-control"></a>Zadejte hodnoty do ovládacího prvku pole se seznamem  
  
1.  Vyberte ovládací prvek pole se seznamem kliknutím na ni.  
  
2.  V [okno vlastností](/visualstudio/ide/reference/properties-window), přejděte dolů k položce **Data** vlastnost.  
  
    > [!NOTE]
    >  Pokud jsou zobrazení vlastností seskupené podle typu, **Data** se zobrazí v **různé** vlastnosti.  
  
3.  Klikněte v oblasti hodnotu pro **Data** vlastnost a zadejte hodnoty dat, oddělené středníky.  
  
    > [!NOTE]
    >  Neumisťujte mezery mezi hodnotami, protože prostory narušit podle abecedy v rozevíracím seznamu.  
  
4.  Klikněte na tlačítko **Enter** po dokončení přidávání hodnot.  
  
 Informace o zvětšení rozevírací část pole se seznamem, naleznete v tématu [nastavení velikosti pole se seznamem a jeho rozevíracího seznamu](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).  
  
> [!NOTE]
>  Nelze přidat hodnoty k použití tohoto postupu projekty Win32 ( **Data** vlastnost je zobrazena šedě pro projekty Win32). Projekty Win32 knihovny, které přidat tuto funkci nemají, je nutné přidat hodnoty pole se seznamem se projekt Win32 prostřednictvím kódu programu.  
  
### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>K otestování výskytu hodnoty v poli se seznamem  
  
1.  Po zadání hodnoty v **Data** vlastnosti, klikněte na tlačítko **testovací** tlačítko [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).  
  
     Zkuste Posun směrem dolů seznamem celá hodnota. Hodnoty se zobrazí přesně tak, jak jsou zadány v **Data** vlastnost **vlastnosti** okna. Neexistuje žádné pravopisné nebo kontrola malá a velká písmena.  
  
     Stisknutím klávesy **Esc** se vrátíte **dialogové okno** editoru.  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)