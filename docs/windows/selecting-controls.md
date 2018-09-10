---
title: Výběr ovládacích prvků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 82abd52573c35b253e83587a18f2c4531af6bf23
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313127"
---
# <a name="selecting-controls"></a>Výběr ovládacích prvků

Vyberte ovládací prvky na velikost, zarovnání, přesunutí, kopírovat, nebo je odstranit a pak provést operaci, kterou chcete. Ve většině případů je třeba vybrat více než jeden ovládací prvek při použití nástroje pro velikost a zarovnání na [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Při výběru ovládacího prvku, má šedé ohraničení kolem něj plný (aktivní) nebo prázdný (neaktivní) "úchyty," squares malý, který se zobrazí v ohraničení výběru. Když vyberete více ovládacích prvků, dominantního ovládacího prvku má plnou úchyty; všechny ostatní vybrané ovládací prvky mají prázdný úchyty.

Při nastavování velikosti nebo zarovnání více ovládacích prvků **dialogové okno** editor používá "dominantního ovládacího prvku" zjistit, jak se ostatní ovládací prvky velikosti nebo zarovnána. Ve výchozím nastavení dominantní ovládací prvek je první ovládací prvek.

- [Výběr více ovládacích prvků](../windows/selecting-multiple-controls.md)

- [Určení dominantního ovládacího prvku](../windows/specifying-the-dominant-control.md)

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)  
[Ovládací prvky](../mfc/controls-mfc.md)