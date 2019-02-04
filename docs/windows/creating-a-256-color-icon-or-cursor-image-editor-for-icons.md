---
title: Používání palety s 256 barvami (editor obrázků pro ikony)
ms.date: 11/04/2016
helpviewer_keywords:
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
ms.openlocfilehash: 4e2f2c9ce58799756137bb47db42e52c97a43d39
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702892"
---
# <a name="using-the-256-color-palette-image-editor-for-icons"></a>Používání palety s 256 barvami (editor obrázků pro ikony)

Použití **Image** editoru, ikony a kurzory může být velikosti velké (64 × 64) s 256 barev palety lze vybírat. Po vytvoření prostředku, je vybrat styl obrázku zařízení.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-create-a-256-color-icon-or-cursor"></a>Chcete-li vytvořit 256barevných ikony nebo kurzoru

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc a pak zvolte **vložit prostředků** z místní nabídky. (Pokud už máte existující prostředek obrázku v souboru .rc, jako je například kurzoru, kliknete pravým tlačítkem **kurzor** a pak zvolte položku **vložení kurzoru** z místní nabídky.)

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

1. V [vložit prostředek – dialogové okno](../windows/add-resource-dialog-box.md)vyberte **ikonu** nebo **kurzor** a zvolte **nový**.

1. Na **Image** nabídce vyberte možnost **nový obrázek zařízení**.

1. Vyberte požadovaný styl 256 barev obrázku.

## <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Vybrat barvu z palety barev 256 pro velké ikony

Pro kreslení pomocí výběru z palety barev 256, je nutné vybrat barvy z **barvy** paletu [okno barvy](../windows/colors-window-image-editor-for-icons.md).

1. Vyberte velké ikony nebo kurzoru nebo vytvořte novou velké ikony nebo kurzoru.

1. Výběr barvy z 256 barev zobrazených v **barvy** paletu **barvy** okna.

   Barva vybraná se stane aktuální barvu v **barvy** paletu **barvy** okna.

   > [!NOTE]
   > Počáteční paletu 256barevných imagí odpovídá na paletě vrácené `CreateHalftonePalette` rozhraní Windows API. Všechny ikony určený pro prostředí Windows by měl palety můžete zabránit blikání během palety realizace.

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Ikony a kurzory: Prostředky obrázků pro zobrazovací zařízení](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)
