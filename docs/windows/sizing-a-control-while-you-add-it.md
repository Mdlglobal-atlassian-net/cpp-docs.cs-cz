---
title: Změna velikosti ovládacího prvku během jeho přidávání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog box controls [C++], size
- controls [C++], sizing
ms.assetid: 06b1dd2b-0ba1-4e1f-adc3-cb73679f765e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: da998c748a3471f053c922e0a80c33d1526b2055
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313140"
---
# <a name="sizing-a-control-while-you-add-it"></a>Změna velikosti ovládacího prvku během jeho přidávání

### <a name="to-size-a-control-while-you-add-it"></a>Pro nastavení velikosti ovládacího prvku během jeho přidávání

1. Vyberte ovládací prvek v [okno nástrojů](/visualstudio/ide/reference/toolbox).

2. Umístěte ukazatel myši (který se zobrazí jako různé vlasy), kde chcete levého horního rohu nový ovládací prvek bude ve vašem dialogovém okně.

3. Klepněte a podržte tlačítko myši pro ukotvení levého horního rohu ovládacího prvku v dialogovém okně pak přesuňte kurzor doprava a dolů, dokud je ovládací prvek požadovanou velikost.

   > [!NOTE]
   > Ve skutečnosti se dá ukotvit, všechny čtyři rohy požadovaný kresbě ovládací prvek. Tento postup použít jako příklad levém horním rohu.

4. Uvolněte tlačítko myši. Vyrovná ovládacího prvku do dialogového okna v zadanou velikost.

   > [!TIP]
   > Můžete změnit velikost ovládacího prvku po přetažení do dialogových oken přesunutím úchyty pro změnu velikosti ohraničení ovládacího prvku. Další informace najdete v tématu [velikosti jednotlivých ovládacích prvků](../windows/sizing-individual-controls.md).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)  
[Přidání obslužných rutin události pro ovládací prvky dialogového okna](../windows/adding-event-handlers-for-dialog-box-controls.md)  
[Ovládací prvky dialogových oken a typy proměnných](../ide/dialog-box-controls-and-variable-types.md)