---
title: Nový prostředek – dialogové okno nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.newtoolbarresource
dev_langs:
- C++
helpviewer_keywords:
- New Toolbar Resource dialog box
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33c63357f0816fbf0d89058d4151ea5785f6f35a
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015017"
---
# <a name="new-toolbar-resource-dialog-box"></a>Dialogové okno Nový prostředek panelu nástrojů
**Nový prostředek panelu nástrojů** dialogové okno umožňuje zadat šířka a výška ohraničení tlačítka, který přidáváte do prostředek panelu nástrojů. Výchozí hodnota je 16 × 15 pixelů.  
  
 Rastrový obrázek, který se používá k vytvoření panelu nástrojů má maximální šířku 2048. Pokud jste nastavili **šířku tlačítka** až 512, můžete mít jenom čtyři tlačítka. Pokud nastavíte šířku na 513, může mít pouze tři tlačítka.  
  
### <a name="button-width"></a>Šířka tlačítka  
 Poskytuje prostor pro zadání šířku pro tlačítka panelu nástrojů, který převádíte z prostředku rastrového obrázku na prostředek panelu nástrojů. Image se ořízne na šířku a výšku zadán a barvy jsou upraveny pro použití standardních barev panelu nástrojů (16 barev).  
  
### <a name="button-height"></a>Výška tlačítka  
 Poskytuje prostor pro zadání výšku pro tlačítka panelu nástrojů, který převádíte z prostředku rastrového obrázku na prostředek panelu nástrojů. Image se ořízne na šířku a výšku zadán a barvy jsou upraveny pro použití standardních barev panelu nástrojů (16 barev).  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Knihovny MFC nebo ATL  
  
## <a name="see-also"></a>Viz také  
 [Vlastnosti tlačítka panelu nástrojů](../windows/toolbar-button-properties.md)   
 [Převádění bitmap na panely nástrojů](../windows/converting-bitmaps-to-toolbars.md)   
 [Editor panelu nástrojů](../windows/toolbar-editor.md)