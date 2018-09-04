---
title: Zobrazení a přidání ovládacích prvků ActiveX do dialogového okna | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.controls.activex
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- Insert ActiveX Control command
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e97393aa6989b7af0a7f3a9a97adaf529f21ba8a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686719"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box"></a>Zobrazení a přidání ovládacích prvků ActiveX do dialogového okna

Visual Studio umožňuje vložit ovládací prvky ActiveX na vašem dialogovém okně.

### <a name="to-see-the-activex-controls-you-have-available"></a>Chcete-li zobrazit ovládací prvky ActiveX, které máte k dispozici

1. Dialogové okno otevřete v editoru dialogového okna.

2. Klikněte pravým tlačítkem kamkoli do těla dialogových oken.

3. V místní nabídce klikněte na tlačítko **vložit ovládací prvek ActiveX**.

   [Dialogové okno Vložit ovládací prvek ActiveX](../windows/insert-activex-control-dialog-box.md) zobrazí všechny ovládací prvky ActiveX v systému. V dolní části dialogového okna se zobrazí cesta k souboru ovládacího prvku ActiveX.

### <a name="to-add-an-activex-control-to-a-dialog-box"></a>Chcete-li přidat ovládací prvek ActiveX do dialogového okna

1. V [dialogové okno Vložit ovládací prvek ActiveX](../windows/insert-activex-control-dialog-box.md), vyberte ovládací prvek, který chcete přidat do vaší dialogového okna a klikněte na tlačítko **OK**.

   Ovládací prvek se zobrazí v dialogovém okně, kde můžete upravit nebo vytvořit pro něj obslužné rutiny, stejně jako jakýkoli jiný ovládací prvek.

   > [!NOTE]
   > Můžete přidat ovládací prvky ActiveX [okno nástrojů](/visualstudio/ide/reference/toolbox).

   > [!CAUTION]
   > Nemusí být možné distribuovat všechny ovládací prvky ActiveX v systému. Přečtěte si licenční smlouvy pro software, který je nainstalovaný ovládací prvky nebo se obraťte na softwarová společnost.

   Můžete umístit ovládací prvky **nástrojů** okno pro snadný přístup. Další informace najdete v tématu [nástrojů](/visualstudio/ide/reference/toolbox).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)  
[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)  
[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)