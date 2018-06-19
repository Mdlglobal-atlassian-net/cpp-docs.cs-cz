---
title: Úprava vlastností ovládacího prvku | Microsoft Docs
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
ms.openlocfilehash: f7976f74e9454b023c4da51168fa780ccaea2342
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873482"
---
# <a name="editing-control-properties"></a>Úprava vlastností ovládacího prvku
### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Úprava vlastností ovládacího prvku nebo ovládací prvky  
  
1.  V dialogovém okně vyberte ovládací prvek, který chcete upravit.  
  
    > [!NOTE]
    >  Pokud vyberete více ovládacích prvků, můžete upravit pouze vlastnosti společné pro vybrané ovládací prvky.  
  
2.  V [vlastnosti – okno](/visualstudio/ide/reference/properties-window), změna vlastností vlastního ovládacího prvku.  
  
    > [!NOTE]
    >  Když nastavíte **rastrový obrázek** vlastnost pro tlačítko, přepínač nebo rovna hodnotě ovládací prvek zaškrtávací políčko **True**, styl bs_bitmap – je implementována pro vlastní ovládací prvek. Další informace najdete v tématu [styly tlačítek](../mfc/reference/styles-used-by-mfc.md#button-styles). Příklad přiřazení rastrový obrázek s ovládacím prvkem naleznete v části [CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Rastrové obrázky se nezobrazí na vlastní ovládací prvek, když jste v editoru dialogového okna prostředků.  
  
### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Chcete-li vrátit zpět změny vlastností ovládacího prvku  
  
1.  Zajistěte, aby že ovládacího prvku má právě fokus, v editoru dialogového okna.  
  
2.  Zvolte **vrátit zpět** z **upravit** nabídky (Pokud není fokus na ovládací prvek, **vrátit zpět** příkaz nebude k dispozici).  
  
 Informace o přidávání zdrojů do spravovaných projekty najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace o ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a prostředky řetězce přiřazení k vlastnosti, najdete v části [návod: lokalizace Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) a [Návod: použití zdrojů pro lokalizaci s technologií ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)

