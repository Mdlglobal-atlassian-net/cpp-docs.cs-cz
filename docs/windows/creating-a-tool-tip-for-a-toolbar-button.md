---
title: Vytvoření popisku tlačítka pro tlačítko Toolbar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [C++], adding to toolbar buttons
- "\nin tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor, creating tool tips
ms.assetid: 0af65342-fd78-4e78-8d0d-dc68f7fc462e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 41c2fa538a7888a2f14ae34fde9133b2872d13ba
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871764"
---
# <a name="creating-a-tool-tip-for-a-toolbar-button"></a>Vytvoření popisku tlačítka pro tlačítko panelu nástrojů
### <a name="to-create-a-tool-tip"></a>Vytvoření popisku tlačítka  
  
1.  Kliknutím na tlačítko panelu nástrojů.  
  
2.  V [vlastnosti – okno](/visualstudio/ide/reference/properties-window)v **výzva** pole vlastnosti, přidejte popis tlačítka pro stavový řádek; po zprávy, přidejte \n a název tip nástroje.  
  
 Běžným příkladem popisku tlačítka je tlačítko Tisk na WordPad:  
  
 1. Spustit program WordPad.  
  
 2. Podržte ukazatel myši nad **tiskových** tlačítka panelu nástrojů.  
  
 3. Všimněte si, že slovo "Tisk" teď se plovoucí pod ukazatele myši.  
  
 4. Podívejte se na stavovém řádku (na velmi dolní části okna WordPad) – Všimněte si, že se nyní zobrazí text "Vytiskne aktivní dokument".  
  
 "Print" v kroku 3 je "tip název nástroj" a 'Vytiskne aktivní dokument' z kroku 4 je "Popis tlačítka pro stavový řádek."  
  
 Pokud chcete tento účinek použití **nástrojů** editor, můžete nastavit **výzva** vlastnost **vytiskne active document\nPrint**.  
  
> [!NOTE]
>  Můžete upravit pomocí text výzvy [vlastnosti – okno](/visualstudio/ide/reference/properties-window).  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Požadavky  
  
 Knihovny MFC nebo knihovny ATL  
  
## <a name="see-also"></a>Viz také  
 [Vytváření, přesunutí a úprava tlačítek panelu nástrojů](../windows/creating-moving-and-editing-toolbar-buttons.md)   
 [Editor panelu nástrojů](../windows/toolbar-editor.md)

