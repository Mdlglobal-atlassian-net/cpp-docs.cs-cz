---
title: Práce s barvou (Editor obrázků pro ikony) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.color
dev_langs:
- C++
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors [C++], Image editor
- colors [C++]
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c829d086198233f0149782f1cb4cb1780aec7ad
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054175"
---
# <a name="working-with-color-image-editor-for-icons"></a>Práce s barvou (editor obrázků pro ikony)

**Editor obrázků** obsahuje řadu funkcí, které konkrétně zpracování a přizpůsobení barev. Můžete nastavit barvu popředí nebo pozadí, vyplnění ohraničené oblasti barvou nebo vybrat barvu na obrázku, který má použít jako aktuální barvu popředí nebo pozadí. Pomocí nástrojů v [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md) spolu s palety barev v [okno barvy](../windows/colors-window-image-editor-for-icons.md) k vytvoření bitové kopie.

Všechny barvy pro monochromatický a 16 barev obrázků jsou uvedeny v **barvy** paletu **barvy** okna. Kromě standardních 16 barev můžete vytvořit své vlastní barvy. Změna barev v paletě okamžitě změnit odpovídající barvu v obrázku.

Při práci s 256 barvami ikonu a obrázky kurzor **barvy** vlastnost v [okno vlastností](/visualstudio/ide/reference/properties-window) se používá. Další informace najdete v tématu [vytváření 256barevných ikony nebo kurzoru s](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md).

> [!NOTE]
> Použití **Editor obrázků**, můžete zobrazit obrázky 32-bit, ale nemůžete je upravovat.

Můžete také vytvořit Image true color. Však true color ukázky nezobrazí úplný paletě v **barvy** okno; zobrazí se pouze v oblasti indikátor barvy popředí nebo pozadí. True barvy se vytvoří s použitím [dialogové okno Výběr vlastních barev](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Další informace najdete v tématu [přizpůsobení nebo změna barev](../windows/customizing-or-changing-colors-image-editor-for-icons.md).

Můžete uložit vlastní barvy palety na disku a načítat je znovu podle potřeby. Palety barev, které jste naposledy použili je uložen v registru a automaticky načte při dalším spuštění sady Visual Studio.

- [Výběr barev popředí nebo pozadí](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)

- [Vyplnění ohraničené oblasti obrázku barvou](../windows/filling-a-bounded-area-of-an-image-with-a-color-image-editor-for-icons.md)

- [Výběr barvy z obrázku, která se použije jinde](../windows/picking-up-a-color-from-an-image-to-use-elsewhere-image-editor-for-icons.md)

- [Výběr průhledného nebo neprůhledného pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)

- [Převrácení barev ve výběru](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)

- [Přizpůsobení nebo změna barev](../windows/customizing-or-changing-colors-image-editor-for-icons.md)

- [Ukládání a načítání různých barevných palet](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)

- [Okno barvy](../windows/colors-window-image-editor-for-icons.md)

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)
