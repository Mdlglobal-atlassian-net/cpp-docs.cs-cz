---
title: "Postupy: vytvoření prostředku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [Visual Studio], creating
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dbf538940bab76559e7cec5a5737ab7661dac1f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-a-resource"></a>Postupy: Vytvoření prostředku
> [!NOTE]
>  Zobrazení prostředků nepodporuje edice Express.  
  
### <a name="to-create-a-new-resource-in-resource-view"></a>Chcete-li vytvořit nový prostředek v zobrazení zdrojů  
  
1.  Se zaměřením na váš soubor .rc v [zobrazení prostředků](../windows/resource-view-window.md), klikněte na tlačítko **upravit** nabídky a zvolte **přidat prostředek** (nebo klikněte pravým tlačítkem na soubor v zobrazení zdrojů a vyberte  **Přidat prostředek** z místní nabídky).  
  
     **Poznámka:** Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  V [dialogové okno Přidat prostředek](../windows/add-resource-dialog-box.md), vyberte typ prostředku, které chcete přidat do projektu.  
  
### <a name="to-create-a-new-resource-in-solution-explorer"></a>Chcete-li vytvořit nový prostředek v Průzkumníku řešení  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na složku projekt a vyberte možnost **přidat**, pak klikněte na tlačítko **přidat prostředek** v místní nabídce.  
  
     Pokud jste již nemají soubor .rc ve vašem projektu, tento krok vytvoří jeden. Potom můžete opakováním tohoto kroku přidejte konkrétní typy prostředků do nového souboru .rc.  
  
2.  V [dialogové okno Přidat prostředek](../windows/add-resource-dialog-box.md), vyberte typ prostředku, které chcete přidat do projektu.  
  
### <a name="to-create-a-new-resource-in-class-view"></a>Chcete-li vytvořit nový prostředek v zobrazení tříd  
  
1.  V [zobrazení tříd](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), klikněte pravým tlačítkem na vaší třídě a zvolte **přidat**, pak klikněte na tlačítko **přidat prostředek** z místní nabídky.  
  
2.  V [dialogové okno Přidat prostředek](../windows/add-resource-dialog-box.md), vyberte typ prostředku, které chcete přidat do projektu.  
  
### <a name="to-create-a-new-resource-from-the-project-menu"></a>Chcete-li vytvořit nový prostředek z nabídky projektu  
  
1.  Z **projektu** nabídce zvolte **přidat prostředek**.  
  
 Když vytvoříte nový prostředek, Visual C++ přiřadí jedinečný název, například IDD_Dialog1. ID prostředku můžete přizpůsobit úpravou vlastností pro prostředek v editoru přidružených prostředků nebo v [vlastnosti – okno](/visualstudio/ide/reference/properties-window).  
  
 Můžete vytvořit prostředek jako nový výchozí prostředek (prostředek, který není na základě šablony) nebo jako prostředek vzorované po [šablony](../windows/how-to-use-resource-templates.md).  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.*  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editory prostředků](../windows/resource-editors.md)   
 [Přidat prostředek – dialogové okno](../windows/add-resource-dialog-box.md)