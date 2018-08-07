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
- dialog box controls, editing properties
ms.assetid: 9bdae21d-6dec-4344-a197-2ca4fc46d040
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa1283f90560390f8fc14ee13d1ab022bbeeff11
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39568859"
---
# <a name="editing-control-properties"></a>Úprava vlastností ovládacího prvku
### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Chcete-li upravit vlastnosti ovládacího prvku nebo ovládacích prvků  
  
1.  V dialogovém okně vyberte ovládací prvek, který chcete upravit.  
  
    > [!NOTE]
    >  Pokud vyberete více ovládacích prvků, lze upravit pouze vlastnosti společné pro vybrané ovládací prvky.  
  
2.  V [okno vlastností](/visualstudio/ide/reference/properties-window), změna vlastností ovládacího prvku.  
  
    > [!NOTE]
    >  Při nastavení **rastrový obrázek** vlastnost tlačítko, přepínač nebo rovna hodnotě ovládací prvek zaškrtávací políčko **True**, styl BS_BITMAP je implementována pro ovládací prvek. Další informace najdete v tématu [styly](../mfc/reference/styles-used-by-mfc.md#button-styles). Příklad přidružení rastrový obrázek ovládacího prvku, naleznete v tématu [CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Rastrové obrázky nezobrazí ovládacího prvku při práci v editoru dialogových oken prostředků.  
  
### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Chcete-li vrátit zpět změny vlastností ovládacího prvku  
  
1.  Ujistěte se, že ovládací prvek má fokus v editoru dialogového okna.  
  
2.  Zvolte **zpět** z **upravit** nabídce (pokud fokus není na ovládací prvek, **zpět** příkaz nebude k dispozici).  
  
 Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [návod: lokalizace Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5) a [Návod: použití prostředků for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
## <a name="requirements"></a>Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)