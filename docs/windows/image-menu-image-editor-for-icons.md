---
title: Nabídka obrázku (C++ Editor obrázků pro ikony)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.dialog.GridSettings
- vc.editors.gridsettings
helpviewer_keywords:
- Image menu
- Grid Settings dialog box [C++]
ms.assetid: ac2b4d53-1919-4fd1-a0af-d3c085c45af2
ms.openlocfilehash: e7d7d92401d5910cbb8aba8ab4c6000eca45cb01
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849727"
---
# <a name="image-menu-c-image-editor-for-icons"></a>Nabídka obrázku (C++ Editor obrázků pro ikony)

**Image** nabídky, která se zobrazí pouze tehdy, když **Image** editor není aktivní, obsahuje příkazy pro úpravy obrázků, Správa palet barev a nastavení **Editor obrázků** okna Možnosti. Příkazy pro použití imagí zařízení jsou také k dispozici při práci s ikonami a kurzory.

|Příkaz|Popis|
|---|---|
|**Invertovat barvy**|Invertuje barev. Další informace najdete v tématu [převrácení barev ve výběru](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md).|
|**Flip Horizontal**|Převrátí obrázek nebo výběr vodorovně. Další informace najdete v tématu [překlopení obrázku](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Převrátit svisle**|Převrátí obrázek nebo výběr svisle. Další informace najdete v tématu [překlopení obrázku](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Otočit o 90 stupňů**|Otočí obrázek nebo výběr o 90 stupňů. Další informace najdete v tématu [překlopení obrázku](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Zobrazit okno barev**|Otevře [okno barvy](../windows/colors-window-image-editor-for-icons.md), ve kterém můžete zvolit barev použitých pro vaši image. Další informace najdete v tématu [práce s barvou](../windows/working-with-color-image-editor-for-icons.md).|
|**Použít výběr jako štětce**|Umožňuje vytvořit vlastní štětec z část obrázku. Váš výběr se změní vlastní štětec, který distribuuje barev ve výběru mezi bitovou kopii. Zkopíruje výběr jsou ponechána na cestě přetahování. Tím pomaleji se při přetahování, jsou provedeny další kopie. Další informace najdete v tématu [vytvoření vlastního štětce](../windows/creating-a-custom-brush-image-editor-for-icons.md).|
|**Kopírování a výběr osnovy**|Vytvoří kopii aktuálního výběru a zvýrazní ji. Pokud je barva pozadí obsažen v aktuálním výběru, bude vyloučena Pokud jste [transparentní](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) vybrané.
|**Upravit barvy**|Otevře [výběr vlastní barvy](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md), které umožňuje přizpůsobit barvy, můžete použít pro vaši image. Další informace najdete v tématu [přizpůsobení nebo změna barev](../windows/customizing-or-changing-colors-image-editor-for-icons.md).|
|**Načíst paletu**|Otevře [dialogové okno Načíst barvy palety](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), což vám umožní načíst barvy palety dříve uložený soubor .pal.|
|**Uložit paletu**|Uloží do souboru .pal barvy palety.|
|**Nakreslit neprůhledné**|Pokud je vybráno, změní aktuální výběr neprůhledné. Není-li zaškrtnuto, změní aktuální výběr na průhledný. Další informace najdete v tématu [výběr neprůhledné nebo průhledné pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|**Editor panelu nástrojů**|Otevře [nový prostředek panelu nástrojů – dialogové okno](../windows/new-toolbar-resource-dialog-box.md).|
|**Nastavení mřížky**|Otevře **nastavení mřížky** dialogovému oknu, ve kterém můžete zadat mřížky pro vaši image.|
|**Nový typ obrázku**|Otevře [nový \<zařízení > obrázku dialogové okno](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md). Jedna ikona prostředků může obsahovat několik imagí různých velikostí a windows můžete použít velikost příslušnou položku v závislosti na tom, jak se bude zobrazený. Nový typ zařízení nemění velikost ikony, ale místo toho vytvoří novou image v rámci ikonu. Platí jenom pro ikony a kurzory.|
|**Aktuální typ obrázku ikony nebo kurzoru**|Otevře se podnabídka, který obsahuje seznam prvních dostupné kurzoru nebo ikonu imagí (prvních devět). Poslední příkaz v podnabídce **více...** , otevře [otevřít \<zařízení > obrázku dialogové](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Smazat bitovou kopii**|Odstraní image vybrané zařízení.|
|**Nástroje**|Spustí podnabídku obsahující všechny nástroje, které jsou k dispozici [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md).|

**Nastavení mřížky** dialogové okno umožňuje zadat nastavení mřížky pro vaši image a zobrazí čáry mřížky upravený obrázek. Řádky jsou užitečné pro úpravy image, ale nejsou uloženy v rámci samotné.

|Vlastnost|Popis|
|---|---|
|**Mřížka pixelů**|Pokud je zaškrtnuto, zobrazí v editoru obrázků do mřížky kolem každý pixel. Mřížky se zobrazí pouze na 4 x a vyšších rozlišení.|
|**Mřížka dlaždic**|Při výběru zobrazí v editoru obrázků, určený hodnotami mezery mřížky mřížky kolem bloky v pixelech.|
|**Šířka**|Určuje šířku každého bloku dlaždice. Tato vlastnost je užitečná při kreslení rastrové obrázky, který obsahuje více bitových kopií, které jsou uspořádány v pravidelných intervalech.|
|**Výška**|Určuje výšku každého bloku dlaždice. Tato vlastnost je užitečná při kreslení rastrové obrázky, který obsahuje více bitových kopií, které jsou uspořádány v pravidelných intervalech.|

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také:

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Změna velikosti obrázku](../windows/resizing-an-image-image-editor-for-icons.md)<br/>
[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)