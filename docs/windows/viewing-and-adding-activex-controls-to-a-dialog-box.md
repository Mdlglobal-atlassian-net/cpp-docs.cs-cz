---
title: Zobrazení a přidání ovládacích prvků ActiveX do dialogového okna (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
ms.openlocfilehash: 139407ec1d4e1bfad6bb06854dc24b86ce7014e8
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293608"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box-c"></a>Zobrazení a přidání ovládacích prvků ActiveX do dialogového okna (C++)

Visual Studio umožňuje vložit ovládací prvky ActiveX na vašem dialogovém okně.

**Vložit ovládací prvek ActiveX** dialogové okno umožňuje vložit ovládací prvky ActiveX na vašem dialogovém okně přitom [editoru dialogového okna](../windows/dialog-editor.md). Toto dialogové okno obsahuje následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Ovládací prvek ActiveX**|Zobrazí seznam ovládacích prvků ActiveX. Vložení ovládacího prvku z tohoto dialogového okna negeneruje obálkovou třídu. Pokud potřebujete obálkovou třídu, použijte [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code) si ji vytvořit (Další informace najdete v tématu [přidání třídy](../ide/adding-a-class-visual-cpp.md)). Ovládací prvek ActiveX v tomto seznamu nezobrazí, zkuste nainstalovat ovládací prvek podle pokynů jeho dodavatele.|
|**Cesta**|Zobrazí soubor, ve kterém se nachází v ovládacím prvku ActiveX.|

Můžete umístit ovládací prvky **nástrojů** okno pro snadný přístup. Další informace najdete v tématu [nástrojů](/visualstudio/ide/reference/).

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-see-the-activex-controls-you-have-available"></a>Chcete-li zobrazit ovládací prvky ActiveX, které máte k dispozici

1. Dialogové okno otevřete v editoru dialogového okna.

1. Klikněte pravým tlačítkem kamkoli do těla dialogového okna.

1. V místní nabídce vyberte **vložit ovládací prvek ActiveX**.

   **Vložit ovládací prvek ActiveX** dialogového okna zobrazuje všechny ovládací prvky ActiveX v systému. V dolní části dialogového okna se zobrazí cesta k souboru ovládacího prvku ActiveX.

## <a name="to-add-an-activex-control-to-a-dialog-box"></a>Chcete-li přidat ovládací prvek ActiveX do dialogového okna

1. V **vložit ovládací prvek ActiveX** dialogovém okně vyberte ovládací prvek, který chcete přidat do vaší dialogového okna a vyberte **OK**.

   Ovládací prvek se zobrazí v dialogovém okně, kde můžete upravit nebo vytvořit pro něj obslužné rutiny, stejně jako jakýkoli jiný ovládací prvek.

   > [!NOTE]
   > Můžete přidat ovládací prvky ActiveX [okno nástrojů](/visualstudio/ide/reference/toolbox).

   > [!CAUTION]
   > Nemusí být možné distribuovat všechny ovládací prvky ActiveX v systému. Přečtěte si licenční smlouvy pro software, který je nainstalovaný ovládací prvky nebo se obraťte na softwarová společnost.

   Můžete umístit ovládací prvky **nástrojů** okno pro snadný přístup. Další informace najdete v tématu [nástrojů](/visualstudio/ide/reference/toolbox).

## <a name="to-edit-properties-for-an-activex-control"></a>Postup úpravy vlastností pro ovládací prvek ActiveX

Poskytuje nezávislým výrobcům – ovládací prvky ActiveX mohou jsou vybavené své vlastní vlastnosti a vlastnosti. Vlastnosti pro ovládací prvky ActiveX jsou zobrazeny v **vlastnosti** okna. Kromě toho se zobrazují všechny stránky vlastností vytvořený autorům ovládací prvek ActiveX v **stránky vlastností** dialogové okno (Chcete-li zobrazit **stránku vlastností** pro konkrétní ovládací prvek ActiveX, klikněte na tlačítko  **Stránka vlastností** tlačítko [okno vlastností](/visualstudio/ide/reference/properties-window)).

Různé karty se zobrazí na stránce vlastností pro ovládací prvek ActiveX, v závislosti na seznamy vlastností, které jsou součástí ovládacího prvku ActiveX.

> [!NOTE]
> Následující postup platí pro použitím stránky vlastnosti můžete upravit ovládací prvky ActiveX. Můžete také procházet a upravovat vlastnosti ActiveX na novém **vlastnosti** okna.

1. Vyberte **ActiveX** ovládacího prvku.

1. Na **zobrazení** nabídce vyberte možnost **stránku vlastností** a zobrazte vlastnosti.

1. Proveďte změny podle potřeby na stránce vlastností.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)<br/>
[Zobrazení a přidání ovládacích prvků ActiveX do dialogového okna](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)<br/>
[Karta editoru dialogového okna, panel nástrojů](../windows/dialog-editor-tab-toolbox.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
