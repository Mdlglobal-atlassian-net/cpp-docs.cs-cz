---
title: Vytvoření nabídky (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.menu
helpviewer_keywords:
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: b779e6b089410b818247471086fe987c37b1f36c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518551"
---
# <a name="creating-a-menu-c"></a>Vytvoření nabídky (C++)

> [!NOTE]
> **Okno zdrojů** není k dispozici ve verzích Express.

### <a name="to-create-a-standard-menu"></a>Chcete-li vytvořit standardní nabídky

1. Z **zobrazení** nabídky, klikněte na **zobrazení prostředků** a potom klikněte pravým tlačítkem na **nabídky** záhlaví a zvolte **přidat prostředek**. Zvolte **nabídky**.

2. Vyberte **nová položka** pole (obdélník, který obsahuje "Zde typu") na panelu nabídek.

   ![Nové pole položky v nabídce editoru](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   Nová položka – pole

3. Zadejte název pro vaši novou nabídku, například "File".

   Text, který zadáte, se zobrazí v **nabídky** editoru a **titulek** pole [okno vlastností](/visualstudio/ide/reference/properties-window). Upravit vlastnosti pro vaše nové nabídce v některém umístění.

   Po názvu jste udělili novou nabídku v panelu nabídek, nová položka pole posune doprava (umožňují přidat jiné nabídky) a jiného pole novou položku se otevře pod první nabídky, příkazy nabídky můžete přidat k němu.

   ![Rozbalené pole novou položku](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   Nové položky pole se zaměřením posune po zadejte název nabídky

   > [!NOTE]
   > Chcete-li vytvořit jedné položky nabídky na řádku nabídek, nastavte **automaticky otevírané okno** vlastnost **False**.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor nabídek](../windows/menu-editor.md)