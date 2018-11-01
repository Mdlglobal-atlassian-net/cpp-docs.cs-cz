---
title: Nabídka obrázku (C++ Editor obrázků pro ikony)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
helpviewer_keywords:
- Image menu
ms.assetid: ac2b4d53-1919-4fd1-a0af-d3c085c45af2
ms.openlocfilehash: e015e7d3e814ce4563abc3cc75d7799eb65bd86a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596583"
---
# <a name="image-menu-c-image-editor-for-icons"></a>Nabídka obrázku (C++ Editor obrázků pro ikony)

**Image** nabídky, která se zobrazí pouze tehdy, když **Image** editor není aktivní, obsahuje příkazy pro úpravy obrázků, Správa palet barev a nastavení **Editor obrázků** okna Možnosti. Kromě toho příkazy pro použití imagí zařízení jsou k dispozici při práci s ikonami a kurzory.

- **Invertovat barvy**

   Invertuje barev. Další informace najdete v tématu [převrácení barev ve výběru](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md).

- **Převrátit vodorovně**

   Převrátí obrázek nebo výběr vodorovně. Další informace najdete v tématu [překlopení obrázku](../windows/flipping-an-image-image-editor-for-icons.md).

- **Převrátit svisle**

   Převrátí obrázek nebo výběr svisle. Další informace najdete v tématu [překlopení obrázku](../windows/flipping-an-image-image-editor-for-icons.md).

- **Otočit o 90 stupňů**

   Otočí obrázek nebo výběr o 90 stupňů. Další informace najdete v tématu [překlopení obrázku](../windows/flipping-an-image-image-editor-for-icons.md).

- **Zobrazit okno barev**

   Otevře [okno barvy](../windows/colors-window-image-editor-for-icons.md), ve kterém můžete zvolit barev použitých pro vaši image. Další informace najdete v tématu [práce s barvou](../windows/working-with-color-image-editor-for-icons.md).

- **Použít výběr jako štětce**

   Umožňuje vytvořit vlastní štětec z část obrázku. Váš výběr se změní vlastní štětec, který distribuuje barev ve výběru mezi bitovou kopii. Zkopíruje výběr jsou ponechána na cestě přetahování. Tím pomaleji se při přetahování, jsou provedeny další kopie. Další informace najdete v tématu [vytvoření vlastního štětce](../windows/creating-a-custom-brush-image-editor-for-icons.md).

- **Kopírování a výběr osnovy**

   Vytvoří kopii aktuálního výběru a zvýrazní ji. Je-li barvu pozadí je obsažen v aktuálním výběru, bude vyloučena v případě, že máte [transparentní](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) vybrané.

- **Upravit barvy**

   Otevře [výběr vlastní barvy](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md), které umožňuje přizpůsobit barvy, můžete použít pro vaši image. Další informace najdete v tématu [přizpůsobení nebo změna barev](../windows/customizing-or-changing-colors-image-editor-for-icons.md).

- **Načíst paletu**

   Otevře [dialogové okno Načíst barvy palety](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), což vám umožní načíst barvy palety dříve uložený soubor .pal.

- **Uložit paletu**

   Uloží do souboru .pal barvy palety.

- **Nakreslit neprůhledné**

   Pokud je vybráno, změní aktuální výběr neprůhledné. Není-li zaškrtnuto, změní aktuální výběr na průhledný. Další informace najdete v tématu [výběr neprůhledné nebo průhledné pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

- **Editor panelu nástrojů**

   Otevře [nový prostředek panelu nástrojů – dialogové okno](../windows/new-toolbar-resource-dialog-box.md).

- **Nastavení mřížky**

   Otevře [dialogové okno Nastavení mřížky](../windows/grid-settings-dialog-box-image-editor-for-icons.md) ve kterém můžete zadat mřížky pro vaši image.

- **Nový typ obrázku**

   Otevře [nový \<zařízení > obrázku dialogové okno](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md). Jedna ikona prostředků může obsahovat několik imagí různé velikosti; Windows budou moct použít velikost příslušnou položku v závislosti na tom, jak se bude zobrazený. Nový typ zařízení nemohou měnit velikost ikony, ale místo toho vytvoří novou image v rámci ikonu. Platí jenom pro ikony a kurzory.

- **Aktuální typ obrázku ikony nebo kurzoru**

   Otevře se podnabídka, který obsahuje seznam prvních dostupné kurzoru nebo ikonu imagí (prvních devět). Poslední příkaz v podnabídce **více...** , otevře [otevřít \<zařízení > obrázku dialogové](../windows/open-device-image-dialog-box-image-editor-for-icons.md).

- **Smazat bitovou kopii**

   Odstraní image vybrané zařízení.

- **Nástroje**

   Spustí podnabídku obsahující všechny nástroje, které jsou k dispozici [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)