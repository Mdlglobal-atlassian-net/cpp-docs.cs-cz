---
title: Vytváření nabídek (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.menu
helpviewer_keywords:
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
- menus [C++], adding items
- commands [C++], adding to menus
- menu items, adding to menus
- submenus
- submenus [C++], creating
- menus [C++], creating
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- shortcut menus [C++], connecting to applications
- pop-up menus
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
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: da5fc355ae11ee5efb1c58be9e33bd4fb8bff02d
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320520"
---
# <a name="creating-menus-c"></a>Vytváření nabídek (C++)

> [!NOTE]
> **Okno zdrojů** není k dispozici ve verzích Express.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="create-a-standard-menu"></a>Vytvořit standardní nabídku

1. Z **zobrazení** nabídce vyberte možnost **zobrazení prostředků** a potom klikněte pravým tlačítkem na **nabídky** záhlaví a zvolte **přidat prostředek**. Zvolte **nabídky**.

1. Vyberte **nová položka** pole (obdélník, který obsahuje "Zde typu") na panelu nabídek.

   ![Nové pole položky v nabídce editoru](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   Nová položka – pole

1. Zadejte název pro vaši novou nabídku, například "File".

   Text, který zadáte, se zobrazí v **nabídky** editoru a **titulek** pole [okno vlastností](/visualstudio/ide/reference/properties-window). Upravit vlastnosti pro vaše nové nabídce v některém umístění.

   Po názvu jste udělili novou nabídku v panelu nabídek, nová položka pole posune doprava (umožňují přidat jiné nabídky) a jiného pole novou položku se otevře pod první nabídky, příkazy nabídky můžete přidat k němu.

   ![Rozbalené pole novou položku](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   Nové položky pole se zaměřením posune po zadejte název nabídky

   > [!NOTE]
   > Chcete-li vytvořit jedné položky nabídky na řádku nabídek, nastavte **automaticky otevírané okno** vlastnost **False**.

## <a name="create-a-submenu"></a>Vytvoření podnabídky

1. Vyberte příkaz nabídky, u kterého chcete vytvořit podnabídky.

1. V **nová položka** pole, které se zobrazí napravo, zadejte název nového příkazu nabídky. Tento nový příkaz zobrazí první v nabídce podnabídka.

1. Přidejte další příkazy nabídky podnabídka.

## <a name="to-insert-a-new-menu-between-existing-menus"></a>Chcete-li vložit nové nabídky mezi stávající nabídky

Vyberte existující název nabídky a stiskněte klávesu **vložit** klíč. **Nová položka** pole se vloží před vybranou položku.

   \- nebo –

Klikněte pravým tlačítkem na řádku nabídek a vyberte **vložit nový** z místní nabídky.

## <a name="add-commands-to-a-menu"></a>Přidání příkazů do nabídky

1. Vytvoření nabídky.

1. Vyberte název nabídky, například **souboru**.

   Každá nabídka bude rozbalte a vystavovat nové položky pole pro příkazy. Například můžete přidat příkazy **nový**, **otevřít**, a **Zavřít** k **souboru** nabídky.

1. Do pole nové položky zadejte název pro nový příkaz nabídky.

   > [!NOTE]
   > Text, který zadáte, se zobrazí v **nabídky** editoru a **titulek** pole [okno vlastností](/visualstudio/ide/reference/properties-window). Upravit vlastnosti pro vaše nové nabídce v některém umístění.

   > [!TIP]
   > Můžete definovat přístupové klávesy (Klávesová zkratka), který umožňuje uživateli vybrat příkaz nabídky. Zadejte znak ampersand (`&`) před písmenem určit jako symbol. Uživatel může vybrat příkaz nabídky tak, že zadáte písmeno.

1. V **vlastnosti** okna, vyberte příkaz Vlastnosti, které se vztahují na nabídku. Podrobnosti najdete v tématu [vlastnosti příkazu nabídky](../windows/menu-command-properties.md).

1. V **řádku** pole **vlastnosti** okno, zadejte řetězec výzvy, které se mají zobrazit ve stavovém řádku vaší aplikace.

   Tento krok vytvoří záznam v tabulce řetězců se stejným identifikátorem prostředku jako příkaz, který jste vytvořili.

   > [!NOTE]
   > Výzvy lze použít pouze pro položky nabídky **automaticky otevírané okno** vlastnost **True**. Například položky nabídek nejvyšší úrovně může mít výzvy, pokud mají položky dílčí nabídky. Účel **výzvy** je určit, co se stane, pokud uživatel zvolí položka nabídky.

1. Stisknutím klávesy **Enter** na dokončení příkazu nabídky.

   Nové položky políčko je zaškrtnuto, takže si můžete vytvořit další příkazy.

## <a name="create-pop-up-menus"></a>Vytvořit místní nabídky

[Místní nabídky](../mfc/menus-mfc.md) zobrazení často používané příkazy. Můžou být závislá na kontextu do umístění ukazatele. Pomocí místní nabídky v aplikaci vyžaduje vytváření samotné nabídky a následným připojením ke kódu aplikace.

Po vytvoření prostředku nabídky, kód vaší aplikace potřebuje k načtení prostředku nabídky a použít [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) způsobit v nabídce Zobrazit. Jakmile uživatel má vynechat v rozbalovací nabídce vyberete mimo něj, nebo má vybraný příkaz, který funkce vrátí. Pokud uživatel vybere příkaz, tento příkaz se pošle zpráva v okně, jehož popisovač byl předán.

### <a name="to-create-a-pop-up-menu"></a>Chcete-li vytvořit místní nabídky

1. [Vytvořit nabídku](../windows/creating-a-menu.md) s prázdný název (neposkytují **titulek**).

1. [Přidání příkazu nabídky do nové nabídky](../windows/adding-commands-to-a-menu.md). Přesunout na první příkaz nabídky pod názvem prázdné nabídky (říká dočasné titulek `Type Here`). Zadejte **titulek** a další informace.

   Tento postup opakujte pro další příkazy nabídky v místní nabídce.

1. Uložte prostředek nabídky.

### <a name="to-connect-a-pop-up-menu-to-your-application"></a>Pro připojení místní nabídky k aplikaci

1. Přidání obslužné rutiny zpráv pro WM_CONTEXTMENU (například). Další informace najdete v tématu [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md).

1. Přidejte následující kód do obslužné rutiny zpráv:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md) předané ve zprávě je obslužná rutina v souřadnicovém systému obrazovky.

   > [!NOTE]
   > Připojení místní nabídky k aplikaci vyžaduje knihovny MFC.

### <a name="to-view-a-menu-resource-as-a-pop-up-menu"></a>Chcete-li zobrazit prostředku nabídky jako místní nabídky

Obvykle, když pracujete v **nabídky** editoru, prostředku nabídky se zobrazí jako panel nabídek. Může však mít prostředky nabídky, které jsou přidány do řádku nabídek aplikace, zatímco program běží.

Klikněte pravým tlačítkem na nabídku a zvolte **zobrazit jako místní nabídku** z místní nabídky.

   Tato možnost je pouze zobrazení prioritní a nezmění vaši nabídku.

   > [!NOTE]
   > Chcete-li změnit zpět na zobrazení řádku nabídek klikněte na tlačítko **zobrazit jako místní nabídku** znovu (který odstraněn znak zaškrtnutí barvy a vrátí zobrazení řádku nabídek).

## <a name="edit-multiple-menus-or-menu-commands"></a>Upravit více nabídek nebo příkazů nabídky

### <a name="to-select-multiple-menu-commands"></a>Chcete-li vybrat více příkazů nabídky

Můžete vybrat více názvy nabídek nebo příkazů nabídky ke spuštění hromadné operace, jako je například odstranění nebo změna vlastností.

Když podržíte **Ctrl** klíče, vyberte možnost nabídky a podnabídky příkazy, které chcete.

### <a name="to-move-and-copy-menus-and-menu-commands"></a>Pro přesun a kopírování nabídek a příkazů nabídky

Mohou přesunout nebo kopírovat nabídek a příkazů nabídky pomocí přetahování myší metody nebo pomocí příkazů v místní nabídce (klikněte pravým tlačítkem na nabídky).

#### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>Chcete přesunout nebo kopírovat nabídek nebo příkazů nabídky pomocí přetahování myší – metoda

1. Přetáhněte nebo zkopírujte položku, kterou chcete přejít na:

   - Nové umístění v nabídce aktuální.

   - Jiné nabídky. (Můžete přejít na jiné nabídky přetažením ukazatele myši nad nimi.)

1. Příkaz nabídky vyřaďte, když se vykreslilo vodítko ukazatele zobrazuje umístění, které chcete.

#### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>Chcete přesunout nebo kopírovat nabídek nebo příkazů nabídky pomocí místní nabídky příkazů

1. Klikněte pravým tlačítkem na jeden nebo více nabídek nebo příkazů nabídky.

1. V místní nabídce zvolte **Vyjmout** (k přesunutí) nebo **kopírování**.

1. Pokud přesouváte položky na jiné nabídky prostředků nebo souboru skriptu prostředků [otevřete ho v jiném okně](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

1. Vyberte nabídky nebo příkaz nabídky, že kterou chcete přesunout nebo kopírovat do umístění.

1. V místní nabídce zvolte **vložit**. Položka přesunutý nebo zkopírovaný je umístěn před položku, kterou jste vybrali.

   > [!NOTE]
   > Můžete také přetáhnout, zkopírujte a vložte jiným nabídkám v jiných oknech nabídky.

### <a name="to-delete-a-menu-or-menu-command"></a>Odstranění nabídky nebo příkazu nabídky

1. Klikněte pravým tlačítkem na název nabídky nebo příkaz.

1. Zvolte **odstranit** z místní nabídky.

   > [!NOTE]
   > Podobně můžete použít nabídku provádět další akce, jako je kopírování, vyjmutí, vložení, vložit nový, vložit oddělovač úprav ID zobrazení jako automaticky otevírané okno, zkontrolujte klávesových zkratek apod.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Editor nabídek](../windows/menu-editor.md)