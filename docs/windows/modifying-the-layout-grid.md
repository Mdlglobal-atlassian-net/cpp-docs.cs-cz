---
title: Změna mřížky rozložení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
ms.assetid: ec31f595-7542-485b-806f-efbaeccc1b3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d583bbbfeb4cd426684d1091a165335f7cbb6e64
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441394"
---
# <a name="modifying-the-layout-grid"></a>Změna mřížky rozložení

Pokud jsou uvedení nebo uspořádání ovládacích prvků v dialogovém okně, můžete pro přesnější umístění mřížky rozložení. Po zapnutí mřížky "se přichytil k" tečkované čáry mřížky jakoby zmagnetizovat zobrazí ovládací prvky. Můžete zapnout a vypnout tuto funkci "přichycení k mřížce" a změnit velikost buňky mřížky rozložení.

### <a name="to-turn-the-layout-grid-on-or-off"></a>K zapnutí nebo vypnutí mřížky rozložení

1. Z **formátu** nabídce zvolte **nastavení vodítek**.

2. V [dialogové okno nastavení průvodce](../windows/guide-settings-dialog-box.md)zaškrtněte nebo zrušte **mřížky** tlačítko.

   Můžete řídit mřížky v jednotlivých **dialogové okno** oken editoru pomocí **Přepnout mřížku** tlačítko [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

### <a name="to-change-the-size-of-the-layout-grid"></a>Chcete-li změnit velikost rozložení mřížky

1. Z **formátu** nabídce zvolte **nastavení vodítek**.

2. V [dialogové okno nastavení průvodce](../windows/guide-settings-dialog-box.md), zadejte výšku a šířku dlu buňky v mřížce. Minimální výšku nebo šířku je 4 dlu. Další informace o dlu najdete v tématu [The uspořádání sady ovládacích prvků v dialogových oknech](../windows/arrangement-of-controls-on-dialog-boxes.md).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Stavy editoru dialogových oken (vodítka a mřížky)](../windows/dialog-editor-states-guides-and-grids.md)<br/>
[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)