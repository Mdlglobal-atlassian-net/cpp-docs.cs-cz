---
title: Nastavení ovládacích prvků stejnou šířku, výšku ani velikost | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Make Same Size command
- controls [C++], sizing
ms.assetid: 94b50613-67e2-497b-a2b6-6d98dccfd345
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5077d2dcd426182495cc7a414aca7ca411d1fa60
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605373"
---
# <a name="making-controls-the-same-width-height-or-size"></a>Nastavení stejné šířky, výšky nebo velikosti ovládacích prvků

Změnit velikost skupiny ovládacích prvků na základě velikosti dominantního ovládacího prvku. Můžete také [Změna velikosti ovládacího prvku v závislosti na velikosti jeho text titulku](../windows/sizing-individual-controls.md).

### <a name="to-make-controls-the-same-width-height-or-size"></a>Aby se řídí stejnou šířku, výšku ani velikost

1. [Vyberte ovládací prvky](../windows/selecting-multiple-controls.md) chcete změnit velikost.

   Ovládací prvek nejprve v řadě je dominantního ovládacího prvku. Konečné velikosti ovládacích prvků ve skupině závisí na velikosti dominantního ovládacího prvku. Další informace o výběru dominantního ovládacího prvku, naleznete v tématu [určení dominantního ovládacího prvku](../windows/specifying-the-dominant-control.md).

2. Z **formátu** nabídce zvolte **nastavit stejnou velikost**, pak vyberte jednu z následujících příkazů:

   - **Obojí**

   - **Výška**

   - **Šířka**

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)  
[Ovládací prvky](../mfc/controls-mfc.md)