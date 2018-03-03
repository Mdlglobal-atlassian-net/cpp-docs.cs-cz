---
title: "Postupy: kopírování prostředků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], moving between files
- resources [Visual Studio], copying
- resource files, copying or moving resources between
- resource files, tiling
- .rc files, copying resources between
- rc files, copying resources between
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4ac30e57c0c833f5d26cf9aa8a9ed4ba43946bb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-copy-resources"></a>Postupy: Kopírování prostředků
Prostředky můžete zkopírovat z jednoho souboru do druhého, aniž byste museli měnit je nebo můžete [Změna jazyka nebo podmínky prostředku během kopírování](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md).  
  
 Prostředky můžete snadno zkopírovat z existující prostředek nebo spustitelný soubor do aktuální soubor prostředků. K tomuto účelu můžete otevřít oba soubory obsahující prostředky ve stejnou dobu a přetáhněte položky z jednoho souboru do jiného nebo zkopírujte a vložte mezi těmito dvěma soubory. Tato metoda se dá použít pro soubory skriptu (.rc) prostředků a soubory prostředků šablony (.rct) i spustitelné soubory (.exe).  
  
> [!NOTE]
>  Visual C++ obsahuje ukázkové soubory prostředků, které můžete použít ve své aplikaci. Další informace najdete v tématu [CLIPART: společných prostředků](http://msdn.microsoft.com/en-us/9bac2891-b6b3-49ec-a287-cec850c707e0).  
  
 Můžete použít metodu přetažení myší mezi .rc soubory, které jsou otevřené [mimo projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Kopírování prostředků mezi soubory pomocí metody přetažení myší  
  
1.  Otevřete i samostatné soubory prostředků (Další informace najdete v tématu [zobrazení prostředků v .rc of mimo soubor projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Například otevřete Source1.rc a Source2.rc.  
  
2.  Uvnitř první soubor .rc klikněte na prostředek, který chcete kopírovat. Například v Source1.rc, klikněte na možnost IDD_DIALOG1.  
  
3.  Podržte stisknutou klávesu CTRL a tažením druhý soubor .rc prostředku. Například přetáhněte IDD_DIALOG1 z Source1.rc Source2.rc.  
  
    > [!NOTE]
    >  Přetahování prostředku bez podržíte stisknutou klávesu CTRL Přesune prostředek místo kopírování.  
  
### <a name="to-copy-resources-using-copy-and-paste"></a>Kopírování prostředků pomocí kopírování a vložení  
  
1.  Otevřete i samostatné soubory prostředků (Další informace najdete v tématu [zobrazení prostředků v .rc of mimo soubor projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Například Source1.rc a Source2.rc.  
  
2.  Ve zdrojovém souboru, ze kterého chcete kopírovat prostředek (například Source1.rc), klikněte pravým tlačítkem na prostředek a zvolte **kopie** z místní nabídky.  
  
3.  Klikněte pravým tlačítkem na soubor prostředků, do kterého chcete vložit prostředků (například Source2.rc). Zvolte **vložení** z místní nabídky.  
  
    > [!NOTE]
    >  Nelze přetáhněte a vyřadit, kopírovat, Vyjmout nebo vložte mezi zdrojových souborů v projektu (zobrazení prostředků) a soubory samostatné .rc, (ty otevřít v dokumentu windows). Můžete to udělat v předchozích verzích produktu.  
  
    > [!NOTE]
    >  Aby nedocházelo ke konfliktům s názvy symbolů nebo hodnoty ve existující soubor, Visual C++ změnit hodnotu symbol přenášená prostředků nebo názvu symbolu a hodnota při kopírování na nový soubor.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Postupy: otevření souboru skriptu prostředků mimo projekt (samostatný)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editory prostředků](../windows/resource-editors.md)