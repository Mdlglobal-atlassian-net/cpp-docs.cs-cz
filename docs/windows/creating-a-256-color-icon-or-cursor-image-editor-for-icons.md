---
title: Vytvoření 256barevných ikony nebo kurzoru (Editor obrázků pro ikony) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 256-color palette
- cursors, color
- colors, icons
- colors, cursors
- icons, color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 34336a62574e83a25af5341c753df78be72a6a15
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601680"
---
# <a name="creating-a-256-color-icon-or-cursor-image-editor-for-icons"></a>Vytvoření ikony nebo kurzoru s 256 barvami (editor obrázků pro ikony)

Použití **Image** editoru, ikony a kurzory může být velikosti velké (64 × 64) s 256 barev palety lze vybírat. Po vytvoření prostředku, je vybrat styl obrázku zařízení.

### <a name="to-create-a-256-color-icon-or-cursor"></a>Chcete-li vytvořit 256barevných ikony nebo kurzoru

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc a pak zvolte **vložit prostředků** z místní nabídky. (Pokud už máte existující prostředek obrázku v souboru .rc, jako je například kurzor, můžete můžete jednoduše kliknout pravým tlačítkem **kurzor** a pak zvolte položku **vložení kurzoru** z místní nabídky.)

   > [!NOTE] 
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. V [vložit prostředek – dialogové okno](../windows/add-resource-dialog-box.md)vyberte **ikonu** nebo **kurzor** a klikněte na tlačítko **nový**.

3. Na **Image** nabídky, klikněte na tlačítko **nový obrázek zařízení**.

4. Vyberte požadovaný styl 256 barev obrázku.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Používání palety s 256 barvami](../windows/using-the-256-color-palette-image-editor-for-icons.md)  
[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)  
[Ikony a kurzory: prostředky obrázků pro zobrazovací zařízení](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)