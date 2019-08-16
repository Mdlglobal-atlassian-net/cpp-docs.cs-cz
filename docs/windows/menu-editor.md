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
ms.openlocfilehash: f2a5f1ac63007bf44dc331e2104c6e9e5cac23da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514826"
---
# <a name="menu-editor-c"></a>Editor nabídek (C++)

Nabídky umožňují uspořádat příkazy v logickém a snadno čitelném způsobem. Pomocí **editoru nabídek**můžete vytvářet a upravovat nabídky přímo s panelem nabídek, který se těsně podobá ve vaší dokončené aplikaci.

> [!TIP]
> Při použití **editoru nabídek**můžete v mnoha případech kliknout pravým tlačítkem myši a zobrazit místní nabídku často používaných příkazů. Dostupné příkazy závisí na tom, na čemu ukazatel odkazuje.

## <a name="how-to"></a>Postupy

**Editor nabídek** vám umožní:

### <a name="to-create-a-standard-menu"></a>Vytvoření standardní nabídky

1. Přejděte na **zobrazení** > nabídky**prostředky** a klikněte pravým tlačítkem myši na záhlaví **nabídky** . Zvolte **Přidat prostředek**a pak **Nabídka**.

1. V řádku nabídek vyberte pole **Nová položka** (v tomto poli obsahuje *text*).

   ![Pole Nová položka v editoru nabídek](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   Pole **Nová položka**

1. Zadejte název nové nabídky, například *File*.

   Text, který zadáte, se zobrazí v **editoru nabídek** i v poli **Titulek** v [okně Vlastnosti](/visualstudio/ide/reference/properties-window). Vlastnosti nové nabídky můžete upravit v libovolném umístění.

   Po tom, co máte novou nabídku s názvem na řádku nabídek, se pole Nová položka posune doprava (aby bylo možné přidat další nabídku) a další pole Nová položka se zobrazí pod první nabídkou, abyste do ní mohli přidat příkazy nabídky.

   ![Rozbalené pole nové položky](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   Pole **nové položky** s fokusem se po zadání názvu nabídky přesune nahoru

   > [!NOTE]
   > Chcete-li vytvořit nabídku s jednou položkou na panelu nabídek, nastavte vlastnost **automaticky otevíraná okna** na **hodnotu NEPRAVDA**.

### <a name="to-create-a-submenu"></a>Vytvoření podnabídky

1. Vyberte příkaz nabídky, pro který chcete vytvořit podnabídku.

1. V poli **Nová položka** , která se zobrazí vpravo zadejte název nového příkazu nabídky. Tento nový příkaz se zobrazí jako první v nabídce podnabídky.

1. Přidejte další příkazy nabídky do nabídky podnabídky.

### <a name="to-insert-a-new-menu-between-existing-menus"></a>Vložení nové nabídky mezi existující nabídky

Vyberte název existující nabídky, stiskněte klávesu **INSERT** nebo klikněte pravým tlačítkem myši na panel nabídek a zvolte možnost **Vložit nový**.

   Je vloženo pole **Nová položka** před vybranou položkou.

### <a name="to-add-commands-to-a-menu"></a>Přidání příkazů do nabídky

1. Vytvořte nabídku. Pak vyberte název nabídky, například **soubor**.

   Jednotlivé nabídky rozbalí a zpřístupní nové pole položek pro příkazy. Můžete například přidat příkazy **nové**, **otevřít**a **Zavřít** v nabídce **soubor** .

1. Do pole Nová položka zadejte název nového příkazu nabídky.

   > [!NOTE]
   > Text, který zadáte, se zobrazí v **editoru nabídek** i v poli **Titulek** v [okně Vlastnosti](/visualstudio/ide/reference/properties-window). Vlastnosti nové nabídky můžete upravit v libovolném umístění.

   > [!TIP]
   > Můžete definovat symbolický klíč (klávesovou zkratku), který uživateli umožňuje vybrat příkaz nabídky. Zadejte ampersand (`&`) před písmenem a určete tak jako symbol. Uživatel může vybrat příkaz nabídky zadáním tohoto písmene.

1. V okně **vlastnosti** vyberte vlastnosti příkazu nabídky, které se použijí. Podrobnosti najdete v tématu [vlastnosti příkazu nabídky](../windows/menu-command-properties.md).

1. Do pole **výzvy** v okně **vlastnosti** zadejte řetězec výzvy, který chcete zobrazit ve stavovém řádku vaší aplikace.

   Tento krok vytvoří položku v tabulce řetězců se stejným identifikátorem prostředku jako příkaz nabídky, který jste vytvořili.

   > [!NOTE]
   > Výzvy lze použít pouze pro položky nabídky s **místní** vlastností **true**. Například položky nabídky nejvyšší úrovně mohou mít výzvy, pokud mají položky podnabídky. Účelem **výzvy** je určit, co se stane, když uživatel vybere položku nabídky.

1. Stisknutím klávesy **ENTER** dokončete příkaz nabídky.

   Je vybráno pole Nová položka, abyste mohli vytvořit další příkazy nabídky.

### <a name="to-select-multiple-menu-commands-to-run-bulk-operations-such-as-deleting-or-changing-properties"></a>Chcete-li vybrat více příkazů nabídky ke spuštění hromadných operací, jako je například odstranění nebo změna vlastností

Podržte stisknutou klávesu **CTRL** a vyberte nabídky nebo příkazy podnabídky, které chcete.

### <a name="to-move-and-copy-menus-and-menu-commands"></a>Přesunutí a zkopírování nabídek a příkazů nabídky

- Použijte metodu přetažení:

   1. Přetáhněte nebo zkopírujte položku, na kterou chcete přejít:

      - Nové umístění v aktuální nabídce.

      - Jinou nabídku. Můžete přejít na jiné nabídky přetažením ukazatele myši na ně.

   1. Pokud vodítko pro vložení zobrazuje požadovanou pozici, přetáhněte příkaz nabídky.

- Použijte příkazy místní nabídky:

   1. Klikněte pravým tlačítkem myši na jednu nebo více nabídek nebo příkazů nabídky a pak zvolte **Vyjmout** (pro přesunutí) nebo **Kopírovat**.

   1. Pokud přesouváte položky do jiného prostředku nebo souboru skriptu prostředků nabídky, [otevřete ho v jiném okně](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

   1. Vyberte umístění nabídky nebo příkazu nabídky, do které chcete přesunout nebo kopírovat.

   1. V místní nabídce vyberte možnost **Vložit**. Přesunutá nebo zkopírovaná položka je umístěna před vybranou položkou.

> [!NOTE]
> Můžete také přetahovat, kopírovat a vkládat do jiných nabídek v jiných oknech nabídek.

### <a name="to-delete-a-menu-or-menu-command"></a>Odstranění příkazu nabídky nebo nabídky

Klikněte pravým tlačítkem myši na název nabídky nebo příkaz a vyberte **Odstranit**.

> [!NOTE]
> Podobně můžete použít místní nabídku k provádění dalších akcí, jako je kopírování, vyjmutí, vložení, vložení nového, oddělovač vložení, úprava ID, zobrazení jako automaticky otevíraná okna, zaškrtávací políčka a další.

## <a name="pop-up-menus"></a>Místní nabídky

[Místní nabídky](../mfc/menus-mfc.md) zobrazují často používané příkazy. Můžou být kontextově závislé na umístění ukazatele. Použití místních nabídek ve vaší aplikaci vyžaduje sestavování samotné nabídky a následné připojení k kódu aplikace.

Po vytvoření prostředku nabídky musí kód aplikace načíst prostředek nabídky a použít [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) k zobrazení nabídky. Jakmile uživatel v místní nabídce zavře, vybere mimo ni nebo vybere příkaz, vrátí tato funkce. Pokud uživatel zvolí příkaz, tato zpráva se odešle do okna, jehož popisovač byl předán.

> [!NOTE]
> Pro programy knihovny MFC (Microsoft Foundation Class) a programy ATL použijte **Průvodce kódem** k zavěšení příkazů nabídky do kódu. Další informace najdete v tématu [Přidání události](../ide/adding-an-event-visual-cpp.md) a [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md).

- Chcete-li vytvořit místní nabídku, vytvořte nabídku s prázdným nadpisem a nezadávejte *Titulek*. Pak přidejte příkaz nabídky do nové nabídky, přejděte do prvního příkazu nabídky pod názvem prázdné nabídky, pod kterým je uveden dočasný *typ* titulku, a zadejte *Titulek* a další informace.

   Tento postup opakujte pro všechny další příkazy nabídek v místní nabídce a nezapomeňte uložit prostředek nabídky.

- Chcete-li připojit místní nabídku k aplikaci, například přidat obslužnou rutinu zprávy pro WM_CONTEXTMENU, přidejte následující kód do obslužné rutiny zprávy:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md) předaný obslužnou rutinou zprávy je v souřadnicích obrazovky.

Když pracujete v **editoru nabídek**normálně, zobrazí se jako panel nabídek prostředek nabídky. Je však možné, že máte prostředky nabídky, které jsou přidány do řádku nabídek aplikace v době, kdy je program spuštěn.

- Chcete-li zobrazit prostředek nabídky jako místní nabídku, klikněte pravým tlačítkem myši na nabídku a vyberte možnost **Zobrazit jako automaticky otevírané okno**.

   Tato možnost je pouze preference zobrazení a neupravuje nabídku.

> [!TIP]
> Chcete-li přejít zpět na zobrazení panelu nabídek, vyberte znovu **Zobrazit jako místní** nabídku. Tato akce odebere značku zaškrtnutí a vrátí zobrazení panelu nabídek.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Editory prostředků](../windows/resource-editors.md)<br/>
[Příkazy nabídky](../windows/menu-command-properties.md)<br/>
[Identifikátory objektů uživatelského rozhraní a příkazů](../mfc/user-interface-objects-and-command-ids.md)<br/>
[Nabídky](../mfc/menus-mfc.md)<br/>
[Nabídky](/windows/win32/menurc/menus)