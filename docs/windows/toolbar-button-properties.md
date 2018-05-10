---
title: Vlastnosti tlačítka panelu nástrojů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e61ba7e8720c755ce26408826c56a5c1fc9d51e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="toolbar-button-properties"></a>Vlastnosti tlačítka panelu nástrojů
Vlastnosti tlačítka panelu nástrojů jsou:  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**ID**|Definuje ID pro tlačítko. Rozevíracím seznamu poskytuje společné **ID** názvy.|  
|**Šířka**|Nastaví šířku tlačítko. doporučuje se 16 pixelů.|  
|**Výška**|Nastaví výšku tlačítko. Upozorňujeme, že výška jedno tlačítko změní výšku všechny tlačítek na panelu nástrojů. doporučuje se 15 pixelů.|  
|**řádku**|Definuje zpráva zobrazí ve stavovém řádku. Přidání \n a název přidá popisek tohoto tlačítka panelu nástrojů. Další informace najdete v tématu [vytváření popisek](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|  
  
 **Šířka** a **výška** platí pro všechny tlačítka. Rastrový obrázek, který se používá k vytvoření panelu nástrojů má maximální šířku 2048. Takže pokud nastavíte šířku tlačítko na 512, může mít pouze čtyři tlačítka a pokud nastavíte šířku 513, může mít pouze tři tlačítka.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Knihovny MFC nebo knihovny ATL  
  
## <a name="see-also"></a>Viz také  
 [Změna vlastností tlačítka panelu nástrojů](../windows/changing-the-properties-of-a-toolbar-button.md)   
 [Editor panelu nástrojů](../windows/toolbar-editor.md)

