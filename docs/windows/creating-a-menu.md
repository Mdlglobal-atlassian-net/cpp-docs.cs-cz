---
title: Vytvoření nabídky (C++)
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
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: 438480032f1fe9208e406b4ee499267e42148a48
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702801"
---
# <a name="creating-a-menu-c"></a>Vytvoření nabídky (C++)

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

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor nabídek](../windows/menu-editor.md)