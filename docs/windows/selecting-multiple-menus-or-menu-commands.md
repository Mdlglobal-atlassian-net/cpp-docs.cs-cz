---
title: Úpravy více nabídek nebo příkazů nabídky (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- menu commands [C++], selecting
- menus [C++], selecting
- commands [C++], menu commands
- commands [C++], copying on menus
- menu items, moving
- commands [C++], moving on menus
- menu items, copying
- menu items, deleting
- commands [C++], deleting from menus
- menus [C++], deleting
ms.assetid: b6f17897-2a40-4afd-97d4-a38b7661680b
ms.openlocfilehash: 45e2c4e97dc850b4d6fb13a5526911e4bd5caec2
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703217"
---
# <a name="editing-multiple-menus-or-menu-commands"></a>Úpravy více nabídek nebo příkazů nabídky

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-select-multiple-menu-commands"></a>Chcete-li vybrat více příkazů nabídky

Můžete vybrat více názvy nabídek nebo příkazů nabídky ke spuštění hromadné operace, jako je například odstranění nebo změna vlastností.

Když podržíte **Ctrl** klíče, vyberte možnost nabídky a podnabídky příkazy, které chcete.

## <a name="to-move-and-copy-menus-and-menu-commands"></a>Pro přesun a kopírování nabídek a příkazů nabídky

Mohou přesunout nebo kopírovat nabídek a příkazů nabídky pomocí přetahování myší metody nebo pomocí příkazů v místní nabídce (klikněte pravým tlačítkem na nabídky).

### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>Chcete přesunout nebo kopírovat nabídek nebo příkazů nabídky pomocí přetahování myší – metoda

1. Přetáhněte nebo zkopírujte položku, kterou chcete přejít na:

   - Nové umístění v nabídce aktuální.

   - Jiné nabídky. (Můžete přejít na jiné nabídky přetažením ukazatele myši nad nimi.)

1. Příkaz nabídky vyřaďte, když se vykreslilo vodítko ukazatele zobrazuje umístění, které chcete.

### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>Chcete přesunout nebo kopírovat nabídek nebo příkazů nabídky pomocí místní nabídky příkazů

1. Klikněte pravým tlačítkem na jeden nebo více nabídek nebo příkazů nabídky.

1. V místní nabídce zvolte **Vyjmout** (k přesunutí) nebo **kopírování**.

1. Pokud přesouváte položky na jiné nabídky prostředků nebo souboru skriptu prostředků [otevřete ho v jiném okně](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

1. Vyberte nabídky nebo příkaz nabídky, že kterou chcete přesunout nebo kopírovat do umístění.

1. V místní nabídce zvolte **vložit**. Položka přesunutý nebo zkopírovaný je umístěn před položku, kterou jste vybrali.

   > [!NOTE]
   > Můžete také přetáhnout, zkopírujte a vložte jiným nabídkám v jiných oknech nabídky.

## <a name="to-delete-a-menu-or-menu-command"></a>Odstranění nabídky nebo příkazu nabídky

1. Klikněte pravým tlačítkem na název nabídky nebo příkaz.

1. Zvolte **odstranit** z místní nabídky.

   > [!NOTE]
   > Podobně můžete použít nabídku provádět další akce, jako je kopírování, vyjmutí, vložení, vložit nový, vložit oddělovač úprav ID zobrazení jako automaticky otevírané okno, zkontrolujte klávesových zkratek apod.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor nabídek](../windows/menu-editor.md)