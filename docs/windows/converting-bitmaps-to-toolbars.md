---
title: Převádění bitmap na panely nástrojů (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.newtoolbarresource
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
ms.openlocfilehash: 31b684ff72e970a6b09748b3925564b0b372d339
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702697"
---
# <a name="converting-bitmaps-to-toolbars-c"></a>Převádění bitmap na panely nástrojů (C++)

Můžete vytvořit nový panel nástrojů v projektu jazyka C++ převedením rastrový obrázek. Obrázek z rastrového obrázku se převede na obrázky tlačítek pro panel nástrojů. Obvykle rastrový obrázek obsahuje několik imagí tlačítko v jediné bitmapě pomocí jedné image pro každé tlačítko. Image může mít libovolnou velikost; Výchozí hodnota je 16 pixelů na šířku a výšku obrázku. Můžete zadat velikost Image tlačítko **nový prostředek panelu nástrojů** dialogové okno při výběru **panelu nástrojů editoru** z **Image** nabídky v editoru obrázků.

**Nový prostředek panelu nástrojů** dialogové okno umožňuje zadat šířka a výška ohraničení tlačítka, které přidáváte do nástrojů prostředku v projektu jazyka C++. Výchozí hodnota je 16 × 15 pixelů.

Rastrový obrázek, který se používá k vytvoření panelu nástrojů má maximální šířku 2048. Pokud jste nastavili **šířku tlačítka** až 512, můžete mít jenom čtyři tlačítka. Pokud nastavíte šířku na 513, může mít pouze tři tlačítka.

Dialogové okno má následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Šířka tlačítka**|Poskytuje prostor pro zadání šířku pro tlačítka panelu nástrojů, které při převádění z prostředku rastrového obrázku na prostředek panelu nástrojů. Image se ořízne na šířku a výšku zadán a barvy jsou upraveny pro použití standardních barev panelu nástrojů (16 barev).|
|**Výška tlačítka**|Poskytuje prostor pro zadání výšku pro tlačítka panelu nástrojů, které při převádění z prostředku rastrového obrázku na prostředek panelu nástrojů. Image se ořízne na šířku a výšku zadán a barvy jsou upraveny pro použití standardních barev panelu nástrojů (16 barev).|

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-convert-bitmaps-to-a-toolbar"></a>Převod bitmap na panelu nástrojů

1. Otevřete existující prostředek rastrového obrázku v [editor obrázků](../windows/image-editor-for-icons.md). (Pokud ještě rastrového obrázku není v souboru .rc, klikněte pravým tlačítkem na soubor .rc, zvolte **Import** z místní nabídky, přejděte na rastrový obrázek, které chcete přidat do souboru .rc a pak vyberte **otevřít**.)

1. Z **Image** nabídce zvolte **panelu nástrojů editoru**.

   **Nový prostředek panelu nástrojů** zobrazí se dialogové okno. Můžete změnit šířku a výšku obrázky ikon tak, aby odpovídaly rastrového obrázku. Obrázek panelu nástrojů se následně zobrazí v editoru panelu nástrojů.

1. K dokončení převodu, změňte příkaz **ID** pomocí tlačítka [okno vlastností](/visualstudio/ide/reference/properties-window). Zadejte nový **ID** nebo vyberte **ID** z rozevíracího seznamu.

   > [!TIP]
   > **Vlastnosti** okno obsahuje tlačítko připínáčku v záhlaví programu. Výběrem tohoto tlačítka povolí nebo zakáže **automaticky skrýt** okna. Rychle procházet všechny vlastnosti tlačítka panelu nástrojů bez nutnosti znovu otevřít windows jednotlivých vlastností, zapněte **automaticky skrýt** vypnout proto **vlastnosti** okno zůstane bez pohybu.

Identifikátory příkazů tlačítka na nový panel nástrojů můžete také změnit pomocí [okno vlastností](/visualstudio/ide/reference/properties-window). Informace o úpravách nový panel nástrojů najdete v tématu [vytváření, přesouvání a úprava tlačítek panelu nástrojů](../windows/creating-moving-and-editing-toolbar-buttons.md).

## <a name="requirements"></a>Požadavky

Knihovny MFC nebo ATL

## <a name="see-also"></a>Viz také

[Vytváření nových panelů nástrojů](../windows/creating-new-toolbars.md)<br/>
[Editor panelu nástrojů](../windows/toolbar-editor.md)<br/>
[Vlastnosti tlačítka panelu nástrojů](../windows/toolbar-button-properties.md)<br/>
