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
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: e3b3cc58b82f68c55ac98601fd11775422c901e5
ms.sourcegitcommit: 5a7dbd640376e13379f5d5b2cf66c4842e5e737b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905768"
---
# <a name="creating-menus-c"></a>Vytváření nabídek (C++)

> [!NOTE]
> **Okno zdrojů** není k dispozici ve verzích Express.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-create-a-standard-menu"></a>Chcete-li vytvořit standardní nabídky

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

## <a name="to-create-a-submenu"></a>Vytvoření podnabídky

1. Vyberte příkaz nabídky, u kterého chcete vytvořit podnabídky.

1. V **nová položka** pole, které se zobrazí napravo, zadejte název nového příkazu nabídky. Tento nový příkaz zobrazí první v nabídce podnabídka.

1. Přidejte další příkazy nabídky podnabídka.

## <a name="to-insert-a-new-menu-between-existing-menus"></a>Chcete-li vložit nové nabídky mezi stávající nabídky

Vyberte existující název nabídky a stiskněte klávesu **vložit** klíč. **Nová položka** pole se vloží před vybranou položku.

   \- nebo –

Klikněte pravým tlačítkem na řádku nabídek a vyberte **vložit nový** z místní nabídky.

## <a name="to-add-commands-to-a-menu"></a>Chcete-li přidat do nabídky příkazů

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

## <a name="to-create-pop-up-menus"></a>Chcete-li vytvořit místní nabídky

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

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Editor nabídek](../windows/menu-editor.md)