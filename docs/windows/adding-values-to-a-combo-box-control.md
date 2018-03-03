---
title: "Přidání hodnot do ovládacího prvku pole se seznamem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9125ad60648f6f867e1214763a6af164d0239a04
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-values-to-a-combo-box-control"></a>Přidání hodnot do ovládacího prvku pole se seznamem
Přidáním hodnoty do ovládacího prvku pole se seznamem, dokud máte otevřete dialogové okno editor.  
  
> [!TIP]
>  Je vhodné přidat všechny hodnoty do pole se seznamem *před* velikost pole v editoru dialogového okna, nebo může zkrátit text, který by se měla objevit v ovládacím prvku pole se seznamem.  
  
#### <a name="to-enter-values-into-a-combo-box-control"></a>K zadání hodnot do ovládacího prvku pole se seznamem  
  
1.  Vyberte ovládacího prvku pole se seznamem na ni kliknete.  
  
2.  V [vlastnosti – okno](/visualstudio/ide/reference/properties-window), přejděte dolů k položce **Data** vlastnost.  
  
    > [!NOTE]
    >  Pokud jsou zobrazení vlastností, které jsou seskupeny podle typu, **Data** se zobrazí v **různé** vlastnosti.  
  
3.  Klikněte v oblasti hodnotu pro **Data** vlastnosti a pak zadejte svoje data hodnoty oddělené středníky.  
  
    > [!NOTE]
    >  Nevkládejte mezery mezi hodnotami, protože prostory narušovat podle abecedy v rozevíracím seznamu.  
  
4.  Klikněte na tlačítko **Enter** po dokončení přidávání hodnot.  
  
 Informace o zvětšení části rozevíracím seznamem najdete v tématu [nastavení velikosti pole se seznamem a její rozevíracího seznamu](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).  
  
> [!NOTE]
>  Hodnoty nelze přidat do Win32 projektů pomocí tohoto postupu ( **Data** vlastnost není k dispozici pro projekty Win32). Protože projekty Win32 nemají knihovny, které přidat další možnost, je nutné přidat hodnoty pole se seznamem s projektem Win32 prostřednictvím kódu programu.  
  
#### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>K testování vzhled hodnoty v poli se seznamem  
  
1.  Po zadání hodnot v **Data** vlastnosti, klikněte na tlačítko **Test** na tlačítko [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).  
  
     Zkuste posouvání v seznamu dolů na celé hodnoty. Hodnoty se zobrazí přesně tak, jak jsou zadány v **Data** vlastnost v okně Vlastnosti. Neexistuje žádné pravopis nebo kontrola malá a velká písmena.  
  
     Stisknutím klávesy ESC se vraťte do pole editoru dialogových oken.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

