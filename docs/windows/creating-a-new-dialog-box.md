---
title: Vytvoření nového dialogového okna | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, creating
- Dialog editor, creating dialog boxes
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8cd214cdf2a3d4677464c98ca1c950a5c1891a42
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584153"
---
# <a name="creating-a-new-dialog-box"></a>Vytvoření nového dialogového okna

### <a name="to-create-a-new-dialog-box"></a>K vytvoření nového dialogového okna

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc a pak zvolte **přidat prostředek** z místní nabídky.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. V **přidat prostředek** dialogu **dialogové okno** v **typ prostředku** seznamu a potom klikněte na **nový**.

   Pokud symbol plus (**+**) se zobrazí vedle **dialogové okno** typ prostředku, znamená to, že pole šablon dialogového okna jsou k dispozici. Klikněte na znaménko plus rozbalit seznam šablon, vyberte šablonu a klikněte na **nový**.

   Otevře se dialogové okno Nový v **dialogové okno** editoru.

   Můžete také [otevřete existující dialogových oknech v editoru dialogové okno pro úpravy](../windows/viewing-and-editing-resources-in-a-resource-editor.md).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Postupy: Vytvoření prostředku](../windows/how-to-create-a-resource.md)  
[Soubory prostředků](../windows/resource-files-visual-studio.md)  
[Editor dialogových oken](../windows/dialog-editor.md)