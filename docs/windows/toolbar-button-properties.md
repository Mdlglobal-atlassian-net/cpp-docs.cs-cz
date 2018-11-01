---
title: Vlastnosti tlačítka panelu nástrojů (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
ms.assetid: b2705814-7c5d-4f24-8f77-07559b0cdda2
ms.openlocfilehash: f20556ac088180ceb1ed979c3e02ffc465b41c7b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665367"
---
# <a name="toolbar-button-properties-c"></a>Vlastnosti tlačítka panelu nástrojů (C++)

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

[Změna vlastností tlačítka panelu nástrojů](../windows/changing-the-properties-of-a-toolbar-button.md)<br/>
[Editor panelu nástrojů](../windows/toolbar-editor.md)