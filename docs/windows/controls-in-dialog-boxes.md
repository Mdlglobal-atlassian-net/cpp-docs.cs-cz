---
title: "Ovládací prvky v dialogových oknech | Microsoft Docs"
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
- controls [C++], dialog boxes
- dialog box controls, about dialog box controls
- dialog box controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 02ca3523de9341c14d2e2a9837ba84f5625a3379
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="controls-in-dialog-boxes"></a>Ovládací prvky v dialogových oknech
Ovládací prvky můžete přidat pomocí dialogu pole [Karta Editor dialogového okna](../windows/dialog-editor-tab-toolbox.md) v [okno sady nástrojů](/visualstudio/ide/reference/toolbox), který umožňuje volbu ovládacího prvku chcete a přetáhněte ji na dialogové okno. Ve výchozím okno sady nástrojů nastavena na automatické skrýt. Při otevření editoru dialogových oken, zobrazí se jako karty na levém okraji řešení. Však můžete Připnout okno sady nástrojů do pozice kliknutím **automaticky skrýt** tlačítko v pravém horním rohu okna. Další informace o tom, jak řídit chování tohoto okna najdete v tématu [Správa oken](/visualstudio/ide/customizing-window-layouts-in-visual-studio).  
  
 Nejrychlejší způsob, jak přidání ovládacích prvků do dialogového okna, přemístit stávající ovládací prvky nebo přesunutí ovládacích prvků z jednoho dialogové okno na jiný, je použít metodu přetažení myší. Umístění ovládacího prvku v tečkovaná čára jsou uvedeny, dokud je vyřazeno do dialogových oken. Po přidání ovládacího prvku do dialogového okna s metodou přetažení myší řízení přidělena standardní výšce pro daný typ ovládacího prvku.  
  
 Při přidání ovládacího prvku do dialogového okna nebo jiného umístění, jeho posledním umístění může určit příruček nebo okraje, nebo jestli máte mřížky rozložení zapnutý.  
  
 Po přidání ovládacího prvku do dialogového okna, můžete změnit vlastnosti, například jeho popisek v [vlastnosti – okno](/visualstudio/ide/reference/properties-window). Můžete vybrat více ovládacích prvků a změnit jejich vlastnosti najednou.  
  
-   [Přidání, úprava nebo odstranění ovládacích prvků](adding-editing-or-deleting-controls.md)  
  
-   [Výběr ovládacích prvků](../windows/selecting-controls.md)  
  
-   [Změna velikosti jednotlivých ovládacích prvků](../windows/sizing-individual-controls.md)  
  
-   [Nastavení stejné šířky, výšky nebo velikosti ovládacích prvků](../windows/making-controls-the-same-width-height-or-size.md)  
  
-   [Nastavení velikosti pole se seznamem a jeho rozevíracího seznamu](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)  
  
-   [Přidání hodnot do ovládacího prvku pole se seznamem](../windows/adding-values-to-a-combo-box-control.md)  
  
-   [Nastavení šířky vodorovného posuvníku](../windows/setting-the-width-of-a-horizontal-scroll-bar.md)  
  
-   [Uspořádání ovládacích prvků v dialogových oknech](../windows/arrangement-of-controls-on-dialog-boxes.md)  
  
-   [Vlastní ovládací prvky v editoru dialogových oken](custom-controls-in-the-dialog-editor.md)  
  
-   [Definice klávesových zkratek (přístupové klávesy)](../windows/defining-mnemonics-access-keys.md)  
  
-   [Určení umístění a velikosti dialogového okna](../windows/specifying-the-location-and-size-of-a-dialog-box.md)  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Přidání obslužných rutin událostí pro ovládací prvky dialogové okno](../windows/adding-event-handlers-for-dialog-box-controls.md)   
 [Ovládací prvky dialogové okno a typy proměnných](../ide/dialog-box-controls-and-variable-types.md)   
 [Editor dialogových oken](../windows/dialog-editor.md)

