---
title: Nový panel nástrojů prostředek – dialogové okno (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.newtoolbarresource
helpviewer_keywords:
- New Toolbar Resource dialog box [C++]
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
ms.openlocfilehash: 7c45daeb2c07426918f1a636f4230c1c07026ca2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595920"
---
# <a name="new-toolbar-resource-dialog-box-c"></a>Nový panel nástrojů prostředek – dialogové okno (C++)

**Nový prostředek panelu nástrojů** dialogové okno umožňuje zadat šířka a výška ohraničení tlačítka, které přidáváte do nástrojů prostředků v projektu jazyka C++. Výchozí hodnota je 16 × 15 pixelů.

Rastrový obrázek, který se používá k vytvoření panelu nástrojů má maximální šířku 2048. Pokud jste nastavili **šířku tlačítka** až 512, můžete mít jenom čtyři tlačítka. Pokud nastavíte šířku na 513, může mít pouze tři tlačítka.

### <a name="button-width"></a>Šířka tlačítka

Poskytuje prostor pro zadání šířku pro tlačítka panelu nástrojů, který převádíte z prostředku rastrového obrázku na prostředek panelu nástrojů. Image se ořízne na šířku a výšku zadán a barvy jsou upraveny pro použití standardních barev panelu nástrojů (16 barev).

### <a name="button-height"></a>Výška tlačítka

Poskytuje prostor pro zadání výšku pro tlačítka panelu nástrojů, který převádíte z prostředku rastrového obrázku na prostředek panelu nástrojů. Image se ořízne na šířku a výšku zadán a barvy jsou upraveny pro použití standardních barev panelu nástrojů (16 barev).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Knihovny MFC nebo ATL

## <a name="see-also"></a>Viz také

[Vlastnosti tlačítka panelu nástrojů](../windows/toolbar-button-properties.md)<br/>
[Převádění bitmap na panely nástrojů](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Editor panelu nástrojů](../windows/toolbar-editor.md)