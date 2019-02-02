---
title: Ukládání a načítání různých barevných palet (editor obrázků pro ikony)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.color
- vc.editors.loadcolorpalette
helpviewer_keywords:
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
- color palettes
- Load Palette Colors dialog box [C++]
ms.assetid: 694b6346-e606-4f19-aa01-9b4ceb47f423
ms.openlocfilehash: fd2664407d33d8e3ed594921501b7f80e6c8850b
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560267"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>Ukládání a načítání různých barevných palet (editor obrázků pro ikony)

Můžete uložit a načíst **barvy** paletu, která obsahuje [přizpůsobit barvy](../windows/customizing-or-changing-colors-image-editor-for-icons.md). (Ve výchozím nastavení, **barvy** palety naposledy použité se vyplní automaticky, když spustíte Visual Studio.)

> [!TIP]
> Protože **Image** editor neobsahuje žádný způsob, jak obnovit výchozí **barvy** palety, měli byste uložit výchozí **barvy** palety pod názvem, jako  *Standard.PAL* nebo *default.pal* tak, aby je snadno obnovit výchozí nastavení.

Použít **načíst barvy palety** dialogové okno Načíst palet barev speciální pro použití v projektu jazyka C++. Jsou zahrnuty následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Oblast hledání**|Určuje umístění, ve které chcete najít soubor nebo složku. Vyberte šipku a vybrat jiné umístění nebo vyberte ikonu složky na panelu nástrojů pro posun úrovně výš.|
|**Název souboru**|Poskytuje prostor pro zadání názvu souboru, který chcete otevřít. Pokud chcete rychle vyhledat soubor, který jste dříve otevřeli, vyberte název souboru v rozevíracím seznamu, pokud je k dispozici.<br/><br/>Pokud hledáte souboru, můžete použít hvězdičky (*) jako zástupné znaky. Například můžete zadat \*.\* zobrazíte seznam všech souborů. Můžete také zadat úplnou cestu k souboru, například C:\My Documents\MyColorPalette.pal nebo \\\NetworkServer\MyFolder\MyColorPalette.pal.|
|**Soubory typu**|Seznam typů souborů, které se zobrazí. Paleta (* .pal) je výchozí typ souboru pro palet barev.|

## <a name="to-save-a-custom-colors-palette"></a>Chcete-li uložit vlastní barvy palety

1. Z **Image** nabídce zvolte **Uložit paletu**.

1. Přejděte do adresáře, kam chcete uložit paletu a zadejte název pro paletě.

1. Vyberte **Uložit**.

## <a name="to-load-a-custom-colors-palette"></a>Načíst vlastní barvy palety

1. Z **Image** nabídce zvolte **načíst paletu**.

1. V **načíst barvy palety** dialogové okno, přejděte na správný adresář a vyberte paletu chcete načíst. **Barva** palety se uloží s příponou souboru .pal.

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)