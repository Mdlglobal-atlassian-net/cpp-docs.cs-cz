---
title: Zákaz vodítek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- guides, disabling snapping
- Dialog editor [C++], snap to guides
- snap to guides (Dialog editor)
- controls [C++], snap to guides/grid
ms.assetid: 51efa07b-8684-474e-a0b4-191ec5d91d1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1e3ae2e982ce04743644f9c94d9c163478c0b67e
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313114"
---
# <a name="disabling-guides"></a>Zákaz vodítek

Speciální klávesy ve spojení s myši můžete zakázat přichycení efekt vodítka. Použití **Alt** klíč zakáže přichycení efekty v průvodci vybrali. Přesunutí průvodce s **Shift** klíč zabraňuje přesunutí s příručkou Přichycený ovládací prvek.

### <a name="to-disable-the-snapping-effect-of-the-guides"></a>Chcete-li zakázat přichycení efekt vodítka

1. Přetáhněte ovládací prvek při podržení **Alt** klíč.

### <a name="to-move-guides-without-moving-the-snapped-controls"></a>Chcete-li přesunout vodítka bez přesouvání Přichycený ovládací prvky

1. Přetáhněte vodítko při podržení **Shift** klíč.

### <a name="to-turn-off-the-guides"></a>Chcete-li vypnout vodítka

1. Z **formátu** nabídce zvolte **nastavení vodítek**.

2. V [dialogové okno nastavení průvodce](../windows/guide-settings-dialog-box.md)v části **vodítka rozložení**vyberte **žádný**.

   > [!NOTE]
   > Můžete také dvakrát kliknout na panelu pravítko pro přístup k **nastavení vodítek** dialogové okno.

\- nebo –

- Na **formátu** nabídky, klikněte na tlačítko **průvodce přepínací tlačítko**.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Stavy editoru dialogových oken (vodítka a mřížky)](../windows/dialog-editor-states-guides-and-grids.md)  
[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)