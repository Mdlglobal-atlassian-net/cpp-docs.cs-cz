---
title: Úprava vlastností ovládacího prvku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls [C++], editing properties
ms.assetid: 9bdae21d-6dec-4344-a197-2ca4fc46d040
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f0f387f536e5d1762f3c48a1955b5053e144e3bc
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082853"
---
# <a name="editing-control-properties"></a>Úprava vlastností ovládacího prvku

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Chcete-li upravit vlastnosti ovládacího prvku nebo ovládacích prvků

1. V dialogovém okně vyberte ovládací prvek, který chcete upravit.

   > [!NOTE]
   > Pokud vyberete více ovládacích prvků, lze upravit pouze vlastnosti společné pro vybrané ovládací prvky.

2. V [okno vlastností](/visualstudio/ide/reference/properties-window), změna vlastností ovládacího prvku.

   > [!NOTE]
   > Při nastavení **rastrový obrázek** vlastnost tlačítko, přepínač nebo rovna hodnotě ovládací prvek zaškrtávací políčko **True**, styl BS_BITMAP je implementována pro ovládací prvek. Další informace najdete v tématu [styly](../mfc/reference/styles-used-by-mfc.md#button-styles). Příklad přidružení rastrový obrázek ovládacího prvku, naleznete v tématu [CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Rastrové obrázky nezobrazí ovládacího prvku při práci v **dialogové okno** editor prostředků.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Chcete-li vrátit zpět změny vlastností ovládacího prvku

1. Ujistěte se, že ovládací prvek má fokus **dialogové okno** editoru.

2. Zvolte **zpět** z **upravit** nabídce (pokud fokus není na ovládací prvek, **zpět** příkaz nebude k dispozici).

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [návod: lokalizace Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)