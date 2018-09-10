---
title: Používání palety s 256 barvami (Editor obrázků pro ikony) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 256-color palette
- colors [C++], icons and cursors
- cursors [C++], color
- color palettes, 256-color
- palettes, 256-color
- icons, color
ms.assetid: 1506ed00-669b-4a21-b1a4-39b6a84a78bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2eeadca20a722cc0e7e63d903f470cb3aced6d32
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313674"
---
# <a name="using-the-256-color-palette-image-editor-for-icons"></a>Používání palety s 256 barvami (editor obrázků pro ikony)

Pro kreslení pomocí výběru z palety barev 256, je nutné vybrat barvy z **barvy** paletu [okno barvy](../windows/colors-window-image-editor-for-icons.md).

### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Vybrat barvu z palety barev 256 pro velké ikony

1. Vyberte velké ikony nebo kurzoru nebo vytvořte novou velké ikony nebo kurzoru.

2. Výběr barvy z 256 barev zobrazených v **barvy** paletu **barvy** okna.

   Barva vybraná se stane aktuální barvu v **barvy** paletu **barvy** okna.

   > [!NOTE]
   > Počáteční paletu 256barevných imagí odpovídá na paletě vrácené `CreateHalftonePalette` rozhraní Windows API. Všechny ikony určený pro prostředí Windows by měl palety můžete zabránit blikání během palety realizace.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)  
[Vytvoření 256barevných ikony nebo kurzoru](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)  
[Ikony a kurzory: prostředky obrázků pro zobrazovací zařízení](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)