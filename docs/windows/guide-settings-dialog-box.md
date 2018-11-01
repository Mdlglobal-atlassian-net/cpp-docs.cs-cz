---
title: Dialogové okno nastavení průvodce (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- DLUs (dialog units)
- Dialog Editor [C++], snap to guides
- grid spacing
- guides, settings
- dialog units (DLUs)
- layout grid in Dialog Editor
- snap to guides (Dialog editor)
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
ms.assetid: 55381e1c-146a-4fa7-b1b3-b1492817615f
ms.openlocfilehash: 2f83acddf0f56225f74961ef31988a5938685b67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483613"
---
# <a name="guide-settings-dialog-box-c"></a>Dialogové okno nastavení průvodce (C++)

## <a name="layout-guides"></a>Vodítka rozložení

Zobrazuje nastavení vodítek rozložení.

### <a name="none"></a>Žádné

Skryje nástroje rozložení.

### <a name="rulers-and-guides"></a>Pravítka a vodítka

Pokud povolená, přidá do nástroje rozložení; pravítka příručky je možné použít v pravítka. Výchozí příručky jsou okraje, které je možné přesunout přetažením. Klikněte na tlačítko v pravítka umístit průvodce. Ovládací prvky "přichytávat" k Průvodci při přesunutí ovládacích prvků nad nebo vedle sebe. Ovládací prvky také přesunout pomocí průvodce, jakmile jsou k němu připojená. Když ovládací prvek je připojen k vodítko na každé straně a přesunout vodítko, změně velikosti ovládacího prvku.

### <a name="grid"></a>Mřížka

Vytvoří rozložení mřížky. Nové ovládací prvky budou automaticky zarovnat k mřížce.

## <a name="grid-spacing"></a>Rozteč mřížky

Nastavení pro rozteč mřížky se zobrazí v poli jednotky dialogu (dlu).

### <a name="width-dlus"></a>Width: dlu

Nastavuje šířku mřížky rozložení v dlu. Vodorovné DLU je průměrná délka pole písmo dialogového okna dělený čtyři.

### <a name="height-dlus"></a>Height: dlu

Nastaví výšku mřížky rozložení v dlu. Svislé DLU je průměrná výška pole písmo dialogového okna dělený osmidílné série.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Změna mřížky rozložení](../windows/modifying-the-layout-grid.md)<br/>
[Stavy editoru dialogových oken (vodítka a mřížky)](../windows/dialog-editor-states-guides-and-grids.md)