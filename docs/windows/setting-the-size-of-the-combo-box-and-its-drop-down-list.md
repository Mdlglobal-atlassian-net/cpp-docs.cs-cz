---
title: Nastavení velikosti pole se seznamem a jeho rozevíracího seznamu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.combo
dev_langs:
- C++
helpviewer_keywords:
- combo boxes, sizing
- controls [C++], sizing
ms.assetid: 51fb53cf-9ddf-4a20-962e-8553938e55ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8bd2a81c10855dfe1d409b34612956616018dab7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413448"
---
# <a name="setting-the-size-of-the-combo-box-and-its-drop-down-list"></a>Nastavení velikosti pole se seznamem a jeho rozevíracího seznamu

Při přidání do dialogových oken, můžete měnit velikost pole se seznamem. Můžete také určit velikost pole rozevíracího seznamu.

### <a name="to-size-a-combo-box"></a>Pro nastavení velikosti pole se seznamem

1. Vyberte ovládací prvek pole se seznamem ve vašem dialogovém okně.

   Na začátku jsou aktivní pouze vpravo a vlevo úchyty.

2. Pomocí úchytů nastavte šířku pole se seznamem.

Můžete také nastavit velikost svislé rozbalovaná část pole se seznamem.

#### <a name="to-set-the-size-of-the-combo-box-drop-down-list"></a>Nastavení velikosti pole se seznamem pole rozevíracího seznamu

1. Klikněte na tlačítko se šipkou rozevíracího seznamu na pravé straně pole se seznamem.

   ![Šipka na pole se seznamem v projektu knihovny MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Přehled ovládacího prvku změn zobrazíte velikost pole se seznamem s rozevíracího seznamu oblastí extended.

2. Chcete-li změnit počáteční velikost oblasti rozevíracího seznamu použijte dolní úchyt pro změnu velikosti.

   ![Pole se seznamem&#45;nastavení velikosti pole v projektu knihovny MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

3. Klikněte na šipku rozevíracího seznamu zavřete rozevírací část pole se seznamem.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Přidání hodnot do ovládacího prvku pole se seznamem](../windows/adding-values-to-a-combo-box-control.md)<br/>
[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)