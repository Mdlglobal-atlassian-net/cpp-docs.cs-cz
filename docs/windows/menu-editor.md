---
title: Editor nabídek (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.menu.F1
- vc.editors.menu
helpviewer_keywords:
- resource editors [C++], Menu editor
- editors, menus
- Menu editor
- menus [C++], Menu editor
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
ms.assetid: 421fb215-6e12-4ec9-a3af-82d77f87bfa6
ms.openlocfilehash: b5d809fa4e0f608d4c0e6cbdaf8697688c6d3f9c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037273"
---
# <a name="menu-editor-c"></a>Editor nabídek (C++)

Nabídky umožňuje uspořádat příkazy v podobě logické a snadno najít. S **Editor nabídek**, můžete vytvořit a upravit nabídky při práci přímo s panel nabídek, který úzce podobá jedné dokončené aplikace.

> [!TIP]
> Při použití **Editor nabídek**, v mnoha případech je můžete kliknout pravým tlačítkem na Zobrazit místní nabídku s často používanými příkazy. Dostupné příkazy závisí na ukazatel odkazuje na.

## <a name="how-to"></a>Postupy

**Editor nabídek** vám umožní:

### <a name="to-create-a-standard-menu"></a>Chcete-li vytvořit standardní nabídky

1. Přejděte do nabídky **zobrazení** > **zobrazení prostředků** a klikněte pravým tlačítkem na **nabídky** záhlaví. Zvolte **přidat prostředek**, pak **nabídky**.

1. Vyberte **nová položka** pole (obdélníku, který obsahuje *typu tady*) na panelu nabídek.

   ![Nové pole položky v nabídce editoru](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   **Nová položka** pole

1. Například zadejte název vaší nové nabídce *souboru*.

   Text, který zadáte, se zobrazí v **Editor nabídek** a **titulek** pole [okno vlastností](/visualstudio/ide/reference/properties-window). Upravit vlastnosti pro vaše nové nabídce v některém umístění.

   Po názvu jste udělili novou nabídku v panelu nabídek, nová položka pole posune doprava (umožňují přidat jiné nabídky) a jiného pole novou položku se otevře pod první nabídky, příkazy nabídky můžete přidat k němu.

   ![Rozbalené pole novou položku](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   **Nová položka** pole s fokusem posune po zadejte název nabídky

   > [!NOTE]
   > Chcete-li vytvořit jedné položky nabídky na řádku nabídek, nastavte **automaticky otevírané okno** vlastnost **False**.

### <a name="to-create-a-submenu"></a>Vytvoření podnabídky

1. Vyberte příkaz nabídky, u kterého chcete vytvořit podnabídky.

1. V **nová položka** pole, které se zobrazí napravo, zadejte název nového příkazu nabídky. Tento nový příkaz zobrazí první v nabídce podnabídka.

1. Přidejte další příkazy nabídky podnabídka.

### <a name="to-insert-a-new-menu-between-existing-menus"></a>Chcete-li vložit nové nabídky mezi stávající nabídky

Vyberte existující název nabídky a stiskněte klávesu **vložit** klíče, nebo klikněte pravým tlačítkem na řádku nabídek a zvolte **vložit nový**.

   **Nová položka** pole se vloží před vybranou položku.

### <a name="to-add-commands-to-a-menu"></a>Chcete-li přidat do nabídky příkazů

1. Vytvoření nabídky. Vyberte název nabídky, například **souboru**.

   Každá nabídka bude rozbalte a vystavovat nové položky pole pro příkazy. Například můžete přidat příkazy **nový**, **otevřít**, a **Zavřít** k **souboru** nabídky.

1. Do pole nové položky zadejte název pro nový příkaz nabídky.

   > [!NOTE]
   > Text, který zadáte, se zobrazí v **Editor nabídek** a **titulek** pole [okno vlastností](/visualstudio/ide/reference/properties-window). Upravit vlastnosti pro vaše nové nabídce v některém umístění.

   > [!TIP]
   > Můžete definovat přístupové klávesy (Klávesová zkratka), který umožňuje uživateli vybrat příkaz nabídky. Zadejte znak ampersand (`&`) před písmenem určit jako symbol. Uživatel může vybrat příkaz nabídky tak, že zadáte písmeno.

1. V **vlastnosti** okna, vyberte příkaz Vlastnosti, které se vztahují na nabídku. Podrobnosti najdete v tématu [vlastnosti příkazu nabídky](../windows/menu-command-properties.md).

1. V **řádku** pole **vlastnosti** okno, zadejte řetězec výzvy, které se mají zobrazit ve stavovém řádku vaší aplikace.

   Tento krok vytvoří záznam v tabulce řetězců se stejným identifikátorem prostředku jako příkaz, který jste vytvořili.

   > [!NOTE]
   > Výzvy lze použít pouze pro položky nabídky **automaticky otevírané okno** vlastnost **True**. Například položky nabídek nejvyšší úrovně může mít výzvy, pokud mají položky dílčí nabídky. Účel **výzvy** je určit, co se stane, pokud uživatel zvolí položka nabídky.

1. Stisknutím klávesy **Enter** na dokončení příkazu nabídky.

   Nové položky políčko je zaškrtnuto, takže si můžete vytvořit další příkazy.

### <a name="to-select-multiple-menu-commands-to-run-bulk-operations-such-as-deleting-or-changing-properties"></a>Chcete-li vybrat více příkazů nabídky ke spuštění hromadné operace, jako je například odstranění nebo změna vlastností

Když podržíte **Ctrl** klíče, vyberte možnost nabídky a podnabídky příkazy, které chcete.

### <a name="to-move-and-copy-menus-and-menu-commands"></a>Pro přesun a kopírování nabídek a příkazů nabídky

- Použijte metodu drag drop:

   1. Přetáhněte nebo zkopírujte položku, kterou chcete přejít na:

      - Nové umístění v nabídce aktuální.

      - Jiné nabídky. Můžete přejít na jiné nabídky přetažením ukazatele myši nad nimi.

   1. Příkaz nabídky vyřaďte, když se vykreslilo vodítko ukazatele zobrazuje umístění, které chcete.

- Použijte příkazy místní nabídky:

   1. Klikněte pravým tlačítkem na jeden nebo více nabídek nebo příkazů nabídky a pak zvolte **Vyjmout** (k přesunutí) nebo **kopírování**.

   1. Pokud přesouváte položky na jiné nabídky prostředků nebo souboru skriptu prostředků [otevřete ho v jiném okně](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

   1. Vyberte nabídky nebo příkaz nabídky, že kterou chcete přesunout nebo kopírovat do umístění.

   1. V místní nabídce zvolte **vložit**. Položka přesunutý nebo zkopírovaný je umístěn před položku, kterou jste vybrali.

> [!NOTE]
> Můžete také přetáhnout, zkopírujte a vložte jiným nabídkám v jiných oknech nabídky.

### <a name="to-delete-a-menu-or-menu-command"></a>Odstranění nabídky nebo příkazu nabídky

Název nabídky nebo příkazu klikněte pravým tlačítkem a zvolte **odstranit**.

> [!NOTE]
> Podobně můžete použít nabídku provádět další akce, jako je kopírování, vyjmutí, vložení, vložit nový, vložit oddělovač úprav ID zobrazení jako automaticky otevírané okno, zkontrolujte klávesových zkratek apod.

## <a name="pop-up-menus"></a>Místní nabídky

[Místní nabídky](../mfc/menus-mfc.md) zobrazení často používané příkazy. Můžou být závislá na kontextu do umístění ukazatele. Pomocí místní nabídky v aplikaci vyžaduje vytváření samotné nabídky a následným připojením ke kódu aplikace.

Po vytvoření prostředku nabídky, kód vaší aplikace potřebuje k načtení prostředku nabídky a použít [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) způsobit v nabídce Zobrazit. Jakmile uživatel má vynechat v rozbalovací nabídce vyberete mimo něj, nebo má vybraný příkaz, který funkce vrátí. Pokud uživatel vybere příkaz, tento příkaz se pošle zpráva v okně, jehož popisovač byl předán.

> [!NOTE]
> Pro programy knihovna tříd MFC (Microsoft Foundation) a knihovny ATL, použijte **průvodců kódem** připojit příkazů nabídky ke kódu. Další informace najdete v tématu [přidání události](../ide/adding-an-event-visual-cpp.md) a [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md).

- Místní nabídka, vytvořte nabídky s prázdný název a neposkytují *titulek*. Potom přidání příkazu nabídky do nové nabídky, přesunout na první příkaz nabídky pod názvem prázdné nabídky s titulkem dočasné *typu tady* a zadejte *titulek* a další informace.

   Tento postup opakujte pro další příkazy nabídky v rozbalovací nabídce a je potřeba uložit nabídce prostředků.

- Připojení místní nabídky do vaší aplikace, například přidání obslužné rutiny zpráv pro WM_CONTEXTMENU a potom přidejte následující kód do obslužné rutiny zpráv:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md) předané ve zprávě je obslužná rutina v souřadnicovém systému obrazovky.

Obvykle, když pracujete v **Editor nabídek**, prostředku nabídky se zobrazí jako panel nabídek. Může však mít prostředky nabídky, které jsou přidány do řádku nabídek aplikace, zatímco program běží.

- Chcete-li zobrazit prostředku nabídky jako místní nabídky, klikněte pravým tlačítkem myši na nabídku a zvolte **zobrazit jako místní nabídku**.

   Tato možnost je pouze zobrazení prioritní a nezmění vaši nabídku.

> [!TIP]
> Chcete-li změnit zpět na zobrazení řádku nabídek vyberte **zobrazit jako místní nabídku** znovu. Tato akce odebere zaškrtávací políčko a vrátí zobrazení řádku nabídek.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Editory prostředků](../windows/resource-editors.md)<br/>
[Příkazy nabídky](../windows/menu-command-properties.md)<br/>

<!--
[User-Interface Objects and Command IDs](../mfc/user-interface-objects-and-command-ids.md)<br/>
[Menus](../mfc/menus-mfc.md)<br/>
[Menus](https://msdn.microsoft.com/library/windows/desktop/ms646977.aspx)-->