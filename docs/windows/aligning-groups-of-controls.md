---
title: Zarovnání skupin ovládacích prvků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], aligning
ms.assetid: a4f49a73-4a17-44b3-8568-aa35f646b5cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c791f2951eb7ac9947d48b563bde624bc3b7979f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393578"
---
# <a name="aligning-groups-of-controls"></a>Zarovnání skupin ovládacích prvků

Následující postup ukazuje, jak zarovnání skupin ovládacích prvků.

### <a name="to-align-groups-of-controls"></a>Zarovnání skupin ovládacích prvků

1. [Vyberte ovládací prvky](../windows/selecting-multiple-controls.md) chcete zarovnat. Vyberte ovládací prvek, který se má provádět dominantního ovládacího prvku nebo nastavit tak, aby se dominantního ovládacího prvku před provádění zarovnání nebo změny velikosti příkazu.

   Konečná pozice skupiny ovládacích prvků, závisí na pozici dominantního ovládacího prvku. Další informace o výběru dominantního ovládacího prvku, naleznete v tématu [určení dominantního ovládacího prvku](../windows/specifying-the-dominant-control.md).

2. Z **formátu** nabídce zvolte **zarovnat**a pak vyberte jednu z následujících zarovnání:

   - `Lefts`: Zarovná vybrané ovládací prvky jejich levé strany.

   - `Centers`: Zarovná vybrané ovládací prvky vodorovně jejich bodů System center.

   - `Rights`: Zarovná vybrané ovládací prvky jejich pravé straně.

   - `Tops`: Zarovná vybrané ovládací prvky jeho horní hrany.

   - `Middles`: Zarovná vybrané ovládací prvky svisle podél jejich střední body.

   - `Bottoms`: Zarovná vybrané ovládací prvky dolního okraje.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Uspořádání ovládacích prvků v dialogových oknech](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)