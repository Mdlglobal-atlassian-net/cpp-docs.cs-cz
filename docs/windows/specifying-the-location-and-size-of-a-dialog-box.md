---
title: Určení umístění a velikosti dialogového okna (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e825dc7b20c0ce75ca1f55fb9ad0310571316a1c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435815"
---
# <a name="specifying-the-location-and-size-of-a-dialog-box-c"></a>Určení umístění a velikosti dialogového okna (C++)

Umístění a velikosti dialogového okna C++, jakož i umístění a velikost ovládacích prvků na ní, se měří v jednotkách dialogového okna. Hodnoty jednotlivých ovládacích prvků a dialogové okno se zobrazí v pravém dolním rohu sady Visual Studio se na stavovém řádku při výběru.

Existují tři vlastnosti, které můžete nastavit [okno vlastností](/visualstudio/ide/reference/properties-window) k určení, kde se zobrazí dialogové okno na obrazovce. **Center** vlastnost je logická hodnota, pokud hodnotu nastavíte na **True**, dialogové okno se vždy zobrazí ve středu obrazovky. Pokud ji nastavíte na **False**, pak můžete nastavit **Pozice_x** a **Pozice_y** explicitně definované tam, kde na obrazovce se zobrazí dialogové okno Vlastnosti. Jsou vlastnosti pozici posunutí hodnoty v levém horním rohu oblasti zobrazení, která je definována jako `{X=0, Y=0}`. Pozice je taky založený na **absolutní zarovnání** vlastnost: Pokud **True**, souřadnice jsou relativní vzhledem k obrazovce; Pokud **False**, souřadnice jsou relativní vzhledem k dialogového okna okno vlastníka.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)