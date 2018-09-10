---
title: Vytvoření průhledných nebo obrácených oblastí v obrázcích zařízení (Editor obrázků pro ikony) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], screen regions
- inverse colors [C++], device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices [C++], transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects [C++], transparent images
- icons [C++], screen regions
ms.assetid: a994954b-b039-4391-a535-58d1fa10fc3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ab57df8151d02064b244212f28fe21628f0f3bb8
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314843"
---
# <a name="creating-transparent-or-inverse-regions-in-device-images-image-editor-for-icons"></a>Vytvoření průhledných nebo obrácených oblastí v obrázcích zařízení (editor obrázků pro ikony)

V [editor obrázků](../windows/image-editor-for-icons.md), počáteční ikony nebo kurzoru bitová kopie má atribut transparentní. I když jsou obdélníkové obrázky ikon a kurzorů, mnoho se nezobrazí, protože části obrázku jsou transparentní; základní image na obrazovce zobrazí prostřednictvím ikony nebo kurzoru. Při přetažení ikonu, části obrázku se může vyskytovat obrácenou barvu. Vytvoření tohoto efektu tak, že nastavíte barvu obrazovky a inverzní barvy v [okno barvy](../windows/colors-window-image-editor-for-icons.md).

Obrazovky a inverzní barvy použijete s ikonami a kurzory tvar a barva odvozené image nebo určují inverzní oblasti. Barvy označující části obrázku má tyto atributy. Můžete změnit barvy, které představují vlastnosti obrazovky a inverzní barev v úpravách. Tyto změny nemají vliv na vzhled ikony nebo kurzoru v aplikaci.

> [!NOTE]
> Dialogová okna a příkazy nabídek, zobrazí se mohou lišit od těch popsaných v **pomáhají** v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-transparent-or-inverse-regions"></a>Vytvoření průhledných nebo obrácených oblastí

1. V **barvy** okna, klikněte na tlačítko **barvy obrazovky** selektor nebo **inverzní barvy** selektor.

2. Použijte na obrazovce nebo inverzní barvy na používání nástroje kreslení obrázku. Další informace o kreslicích nástrojů najdete v tématu [používání nástroje kreslení](using-a-drawing-tool-image-editor-for-icons.md).

### <a name="to-change-the-screen-or-inverse-color"></a>Chcete-li změnit barvu obrazovky nebo inverzní

1. Vyberte buď **barvy obrazovky** selektor nebo **inverzní barvy** selektor.

2. Zvolte barvu z **barvy** paletu **barvy** okna.

   Doplňkovou barvu je automaticky určeno pro ostatní selektor.

   > [!TIP]
   > Pokud dvakrát kliknete **barvy obrazovky** nebo **inverzní barvy** pro výběr [dialogové okno Výběr vlastních barev](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) se zobrazí.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)  
[Ikony a kurzory: prostředky obrázků pro zobrazovací zařízení](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)