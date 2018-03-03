---
title: "Vytvoření nového tlačítka panelu nástrojů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.toolbar
dev_langs:
- C++
helpviewer_keywords:
- Toolbar editor, creating buttons
- toolbar buttons (in Toolbar editor), button image
- toolbar buttons (in Toolbar editor), creating
- toolbar buttons (in Toolbar editor)
ms.assetid: 46c120fe-4f2a-4887-a08f-bd1fea04b3f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6b89d88d931603f1f8dfd65f08cb78210eac19a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-new-toolbar-button"></a>Vytvoření nového tlačítka panelu nástrojů
### <a name="to-create-a-new-toolbar-button"></a>K vytvoření nového tlačítka panelu nástrojů  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md) rozbalte složku prostředků (například Project1.rc).  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Rozbalte **nástrojů** složky a vyberte panelu nástrojů upravit.  
  
3.  ID přiřadíte prázdné tlačítko na pravém konci panelu nástrojů. Můžete to provést úpravou **ID** vlastnost [vlastnosti – okno](/visualstudio/ide/reference/properties-window). Chcete třeba udělit stejné ID jako z nabídky tlačítka panelu nástrojů. V takovém případě použijte pole rozevíracího seznamu vyberte **ID** položky nabídky.  
  
     -nebo-  
  
     Vyberte tlačítko prázdné na pravém konci panelu nástrojů (v podokně zobrazení panelu nástrojů) a začít kreslení. Výchozí tlačítko ID příkazu, který je přiřazen (ID_BUTTON\<n >).  
  
 Můžete také zkopírujte a vložte bitovou kopii na panelu nástrojů jako tlačítko Nový.  
  
#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Chcete-li přidat bitovou kopii na panelu nástrojů jako tlačítka  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md), otevřete poklepáním panelu nástrojů.  
  
2.  Dále otevřete bitovou kopii, kterou chcete přidat na panel nástrojů.  
  
    > [!NOTE]
    >  Pokud v sadě Visual Studio otevřete bitovou kopii, otevře se v editoru obrázků. V ostatních aplikacích grafiky můžete také otevřít bitovou kopii.  
  
3.  Z **upravit** nabídce zvolte **kopie**.  
  
4.  Přepněte na panelu nástrojů kliknutím jeho karty v horní části okna zdroje.  
  
5.  Z **upravit** nabídce zvolte **vložení**.  
  
     Image se zobrazí na panelu nástrojů jako tlačítko Nový.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Požadavky  
 Knihovny MFC nebo knihovny ATL  
  
## <a name="see-also"></a>Viz také  
 [Vlastnosti tlačítka panelu nástrojů](../windows/toolbar-button-properties.md)   
 [Vytváření, přesunutí a úprava tlačítek panelu nástrojů](../windows/creating-moving-and-editing-toolbar-buttons.md)   
 [Editor panelu nástrojů](../windows/toolbar-editor.md)

