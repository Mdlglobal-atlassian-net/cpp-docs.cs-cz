---
title: "Postupy: použití šablon prostředků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- language-specific template files
- resource templates
- resources [Visual Studio], creating
- rct files
- templates, resource templates
- resources [Visual Studio], templates
- .rct files
ms.assetid: bdfe7060-f98e-4859-8285-9c8570360e9d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9bace4f6d8835d9aece7679fa1bb89af3d7a20ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-resource-templates"></a>Postupy: Použití šablon prostředků
Prostředek šablony je vlastní prostředek, který jste uložili jako soubor .rct. Šablony prostředků může potom sloužit jako výchozí bod pro vytvoření další prostředky. Šablony prostředků ušetřit čas při vývoji další prostředky nebo skupiny zdroje, které mají funkce, jako je standardní ovládací prvky a další opakovaných elementy. Například můžete chtít zahrnout tlačítko Nápověda a ikona logo společnosti několik dialogových oken. Uděláte to tak rychle, vytvořte novou šablonu pole dialogové okno a upravit pomocí logo a na tlačítko Nápověda.  
  
 Jakmile jste upravili šablony prostředků, je nutné uložit změny ve složce šablony (nebo libovolného umístění, zadaný v cestě k zahrnutí) tak, aby nové šablony prostředků se zobrazí v části Typ prostředku v [dialogové okno Přidat prostředek](../windows/add-resource-dialog-box.md). Potom můžete nové šablony prostředků tak často, podle potřeby.  
  
> [!NOTE]
>  Soubory specifické pro jazyk šablony můžete umístit v podadresářích adresáře hlavní šablony. Například můžete umístit soubory anglické šablony v \\< adresář šablony prostředků\>\1033.  
  
### <a name="to-create-a-template-for-resources"></a>Chcete-li vytvořit šablonu pro prostředky  
  
1.  V **Průzkumníku**, klikněte pravým tlačítkem na projekt.  
  
2.  V místní nabídce vyberte příkaz **přidat**, pak klikněte na tlačítko **přidat novou položku**.  
  
3.  V **přidat novou položku** dialogovém **šablony:** podokně vyberte **soubor šablony prostředků (.rct)**.  
  
4.  Zadejte název a umístění nového souboru .rct a klikněte na **otevřete**.  
  
5.  Nový soubor .rct se přidá do projektu a zobrazí se v Průzkumníku řešení v části **prostředky** složky.  
  
     Můžete teď poklikejte na soubor .rct a otevře se v okně dokumentu a pak do ní přidejte prostředky (pravým tlačítkem na soubor v okně dokumentu a zvolte **přidat prostředek** z místní nabídky). Pak můžete přizpůsobit tyto prostředky a uložte soubor .rct.  
  
    > [!NOTE]
    >  Když vytvoříte nový soubor RCT –, Visual Studio hledá ho v sadě Visual Studio 9.0\VC\VCResourceTemplates \Program Files\Microsoft, v sadě Visual Studio 9.0\VC\VCResourceTemplates \Program Files\Microsoft\\*LCID* () například 1033 pro angličtinu) a *nebo* na libovolné místo [obsahovat cestu](../windows/how-to-specify-include-directories-for-resources.md). Pokud dáváte přednost RCT – soubory uložené v jiné sdílené složky, například \My dokumenty, stačí tuto složku přidat do cesty zahrnutí a Visual Studio najdete RCT – soubor.  
  
### <a name="to-convert-an-existing-rc-file-to-an-rct-file"></a>Chcete-li převést existující soubor .rc do souboru .rct  
  
1.  [Otevřete soubor .rc jako samostatný soubor](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
2.  Na **soubor** nabídky, klikněte na tlačítko  **Uložit \<* vaše filename*> jako **.  
  
3.  Zadejte umístění a klikněte na tlačítko **OK**.  
  
### <a name="to-create-a-new-resource-from-a-template"></a>Chcete-li vytvořit nový prostředek ze šablony  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md) podokně klikněte pravým tlačítkem na soubor a vyberte **přidat prostředek** z místní nabídky.  
  
2.  V **přidat prostředek** dialogovém okně klikněte na symbol plus (**+**) vedle prostředků pro rozšíření uzlu prostředků a zobrazit všechny šablony, které jsou k dispozici pro tento prostředek.  
  
3.  Dvakrát klikněte na šablonu, kterou chcete použít.  
  
4.  Přidání prostředků upravte podle potřeby v jeho editoru prostředků.  
  
     Editor prostředků automaticky poskytuje jedinečný prostředku. Můžete zkontrolovat, jestli [vlastnosti prostředku](../windows/changing-the-properties-of-a-resource.md) podle potřeby.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.*  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editory prostředků](../windows/resource-editors.md)