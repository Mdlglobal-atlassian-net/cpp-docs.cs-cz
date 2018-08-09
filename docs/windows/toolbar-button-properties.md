---
title: Vlastnosti tlačítka panelu nástrojů | Dokumentace Microsoftu
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
ms.openlocfilehash: a37e15c4235886eef1dbee958ec5c3da29caab0e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650115"
---
# <a name="toolbar-button-properties"></a>Vlastnosti tlačítka panelu nástrojů
Vlastnosti tlačítka panelu nástrojů jsou:  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**ID**|Definuje ID pro tlačítko. Rozevírací seznam obsahuje běžné **ID** názvy.|  
|**Šířka**|Nastavuje šířku tlačítka. doporučuje se 16 pixelů.|  
|**Výška**|Nastaví výšku tlačítka. Všimněte si, že výška tlačítka změní výšku všechna tlačítka na panelu nástrojů. doporučuje se 15 pixelů.|  
|**řádek**|Definuje zprávy zobrazí ve stavovém řádku. Přidání \n a název Přidá popis tlačítka na toto tlačítko panelu nástrojů. Další informace najdete v tématu [vytvoření popisu](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|  
  
 **Šířka** a **výška** platí pro všechna tlačítka. Rastrový obrázek, který se používá k vytvoření panelu nástrojů má maximální šířku 2048. Takže pokud nastavíte šířku tlačítka na 512, můžete mít jenom čtyři tlačítka a nastavte šířku na 513 lze pouze máte tři tlačítka.  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Knihovny MFC nebo ATL  
  
## <a name="see-also"></a>Viz také  
 [Změna vlastností tlačítka panelu nástrojů](../windows/changing-the-properties-of-a-toolbar-button.md)   
 [Editor panelu nástrojů](../windows/toolbar-editor.md)