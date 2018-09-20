---
title: Používání nástroje kreslení (Editor obrázků pro ikony) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.drawing
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0a95d246170776bab20f45e503ba01ca506ce670
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431524"
---
# <a name="using-a-drawing-tool-image-editor-for-icons"></a>Používání nástroje kreslení (editor obrázků pro ikony)

**Image** uživatele od ruky, vykreslování a mazání nástroje všechny fungují stejně jako editor: Vyberte nástroj a v případě potřeby [vyberte barvy popředí a pozadí](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) a možnosti velikosti a tvaru. Přesuňte ukazatel myši na obrázku a kliknutí nebo tažením nakreslete a vymazat.

Když vyberete **gumy** nástroj, **štětce** nástroje, nebo **rozprašovač** nástroji pro výběr možnosti zobrazí možnosti tohoto nástroje.

> [!TIP]
> Namísto použití **gumy** tool, pravděpodobně pro vás bude pohodlnější kreslete barvu pozadí s jedním z nástrojů pro kreslení.

Můžete zvolit buď z nástrojů pro kreslení **Editor obrázků** nástrojů nebo **Image** nabídky.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Vyberte a použijte nástroj pro vykreslování na panelu nástrojů editoru obrázků

1. Klikněte na tlačítko **Editor obrázků** nástrojů.

   - **Gumy** nástroj barvy bitová kopie se aktuální barvu pozadí při stisknutí levého tlačítka myši.

   - **Tužky** nástroj od ruky nakreslí konstantní šířku jeden pixel.

   - **Výběr možnosti určuje velikost a tvar nástroj štětec**.

   - **Rozprašovač** nástroj náhodně distribuuje barev pixelů kolem středu štětce.

        > [!TIP]
        >  Popisy tlačítek se zobrazí, když ukazatel myši najedete myší na tlačítka na [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md). Následující tipy vám umožní identifikovat konkrétní tlačítka uvedeným.

2. V případě potřeby vyberte barvy a štětce:

   - V [barvy palety](../windows/colors-window-image-editor-for-icons.md), klikněte na tlačítko levé tlačítko myši pro výběr barev popředí nebo na tlačítko pravým tlačítkem myši a vyberte barvu pozadí.

   - V [výběr možnosti](../windows/toolbar-image-editor-for-icons.md), klikněte na obrazec představující štětec, který chcete použít.

3. Přejděte na místo na obrázku, kde chcete spustit, kreslení nebo vykreslování. Tvar ukazatele změny podle nástroj, který jste vybrali.

4. Stiskněte klávesu levé tlačítko myši (Barva popředí) nebo pravým tlačítkem myši (pro barvu pozadí) a podržte ho při vykreslení.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Vyberte a používání nástroje kreslení z nabídky Image

1. Klikněte na tlačítko **Image** nabídky a vybereme **nástroje** příkazu.

2. Kaskádové podnabídce zvolte nástroj, který chcete použít.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)<br/>
[Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)