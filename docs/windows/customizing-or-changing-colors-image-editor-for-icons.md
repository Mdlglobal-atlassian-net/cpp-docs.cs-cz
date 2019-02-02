---
title: Přizpůsobení nebo změna barev (editor obrázků pro ikony)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.customcolorselector
helpviewer_keywords:
- dithered color, Image editor
- Custom Color Selector dialog box [C++]
- Image editor [C++], Colors Palette
- colors [C++], image
- bitmaps [C++], colors
- images [C++], colors
- HSL values
- Colors Palette, Image editor
- RGB color values
- Adjust Colors command [C++]
- Image editor [C++], dithered color
ms.assetid: e58f6b32-f435-4d9a-a570-7569433661ae
ms.openlocfilehash: 7ab353ad0aa22c74eeba58e9310d9bc0f8d5a832
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560280"
---
# <a name="customizing-or-changing-colors-image-editor-for-icons"></a>Přizpůsobení nebo změna barev (editor obrázků pro ikony)

**Image** editoru [barvy palety](../windows/colors-window-image-editor-for-icons.md) otevření zobrazí 16 standardní barvy. Zobrazené barvy můžete také vytvořit vlastní barvy. Pak můžete [uložit a načíst vlastní paletu barev](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md).

**Výběr vlastní barvy** dialogové okno umožňuje přizpůsobit barvy, můžete použít pro vaši image. Jsou zahrnuty následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Barevný přechod zobrazení**|Změní hodnoty vybraná barva. Umístěte na křížek na barvu, kterou chcete změnit. Potom přesuňte posuvník nahoru nebo dolů změnu světelnost nebo hodnoty RGB barvy.|
|**Panel světelnost**|Nastaví světelnost pro barvu vyberte v **přechodu barevné zobrazení** pole. Vyberte a přetáhněte bílé šipka nahoru na panelu pro větší jas nebo méně. **Barva** zobrazí vámi zvolená barva a účinnosti světelnost nastavíte.|
|**Barva**|Zobrazí seznam (hodnota barvy kolečko) odstín barvy, které definujete. Hodnoty v rozsahu od 0 do 240, kde 0 je červené, 60 je žlutý, je 120 zelená, 180 je azurová, 200 je purpurová a 240 je modrá.|
|**HUE**|Zobrazí seznam (hodnota barvy kolečko) odstín barvy, které definujete. Hodnoty v rozsahu od 0 do 240, kde 0 je červené, 60 je žlutý, je 120 zelená, 180 je azurová, 200 je purpurová a 240 je modrá.|
|**Po Ne**|Určuje hodnotu sytost barev, které definujete. Sytost je množství barvy v zadané odstín. Hodnoty v rozmezí 0 až 240.|
|**Světelnost**|Zobrazí seznam světelnost (jas) barvy, které definujete. Hodnoty v rozmezí 0 až 240.|
|**Červená**|Určuje červená barva, kterou definujete. Hodnoty v rozsahu od 0 do 255.|
|**Zelená**|Určuje hodnotu zelenou barvu, kterou definujete. Hodnoty v rozsahu od 0 do 255.|
|**Modrá**|Určuje modré hodnotu barvy, které definujete. Hodnoty v rozsahu od 0 do 255.|

## <a name="to-change-colors-on-the-colors-palette"></a>Chcete-li změnit barvy palety barev

1. Z **Image** nabídce zvolte **přizpůsobit barvy**.

1. V **výběr vlastní barvy** dialogového okna, definovat barvu tak, že zadáte hodnoty vyjadřující příslušná textová pole nebo jejich výběr barvy v **přechodu barevné zobrazení** pole.

1. Nastavte světelnost přesunutím posuvníku **světelnost** panelu.

1. Jsou rozloženy mnoho vlastních barev. Pokud chcete plnou barvu nejblíže tónovaná barva, dvakrát klikněte **barva** pole.

   Pokud se později rozhodnete, chcete, aby tónovaná barva, nastavte posuvník **světelnost** pruhu nebo přesunutí mezi vlasy v **přechodu barevné zobrazení** obnovíte rozklad pole.

1. Vyberte **OK** přidáte novou barvu.

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Nabídka obrázku](../windows/image-menu-image-editor-for-icons.md)<br/>
[Okno barvy](../windows/colors-window-image-editor-for-icons.md)