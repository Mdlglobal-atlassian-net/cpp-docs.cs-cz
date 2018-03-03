---
title: "Vlastnosti tlačítka panelu nástrojů | Microsoft Docs"
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
- size, toolbar buttons
- toolbar buttons (in Toolbar editor), setting properties
- Toolbar editor, toolbar button properties
- status bars, active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
ms.assetid: b2705814-7c5d-4f24-8f77-07559b0cdda2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5e179cd400b0b8bcc621a7c69a4814eab098fbaa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="toolbar-button-properties"></a>Vlastnosti tlačítka panelu nástrojů
Vlastnosti tlačítka panelu nástrojů jsou:  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**ID**|Definuje ID pro tlačítko. Rozevíracím seznamu poskytuje společné **ID** názvy.|  
|**Šířka**|Nastaví šířku tlačítko. doporučuje se 16 pixelů.|  
|**Výška**|Nastaví výšku tlačítko. Upozorňujeme, že výška jedno tlačítko změní výšku všechny tlačítek na panelu nástrojů. doporučuje se 15 pixelů.|  
|**Výzva**|Definuje zpráva zobrazí ve stavovém řádku. Přidání \n a název přidá popisek tohoto tlačítka panelu nástrojů. Další informace najdete v tématu [vytváření popisek](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|  
  
 **Šířka** a **výška** platí pro všechny tlačítka. Rastrový obrázek, který se používá k vytvoření panelu nástrojů má maximální šířku 2048. Takže pokud nastavíte šířku tlačítko na 512, může mít pouze čtyři tlačítka a pokud nastavíte šířku 513, může mít pouze tři tlačítka.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Knihovny MFC nebo knihovny ATL  
  
## <a name="see-also"></a>Viz také  
 [Změna vlastností tlačítka panelu nástrojů](../windows/changing-the-properties-of-a-toolbar-button.md)   
 [Editor panelu nástrojů](../windows/toolbar-editor.md)

