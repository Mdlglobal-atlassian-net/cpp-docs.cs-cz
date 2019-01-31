---
title: Zarovnání ovládacích prvků
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
ms.assetid: a4f49a73-4a17-44b3-8568-aa35f646b5cf
ms.openlocfilehash: abfae0f0146fa736a6427eb1180805717ce8a78e
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484978"
---
# <a name="align-controls"></a>Zarovnání ovládacích prvků

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

Následující postupy ukazují, jak Zarovnat ovládací prvky:

## <a name="to-align-groups-of-controls"></a>Zarovnání skupin ovládacích prvků

1. [Vyberte ovládací prvky](../windows/selecting-multiple-controls.md) chcete zarovnat. Vyberte ovládací prvek, který se má provádět dominantního ovládacího prvku nebo nastavit tak, aby se dominantního ovládacího prvku před provádění zarovnání nebo změny velikosti příkazu.

   Konečná pozice skupiny ovládacích prvků, závisí na pozici dominantního ovládacího prvku. Další informace o výběru dominantního ovládacího prvku, naleznete v tématu [určení dominantního ovládacího prvku](../windows/specifying-the-dominant-control.md).

1. Z **formátu** nabídce zvolte **zarovnat**a pak vyberte jednu z následujících zarovnání:

   - `Lefts`: Zarovná vybrané ovládací prvky jejich levé strany.

   - `Centers`: Zarovná vybrané ovládací prvky vodorovně jejich bodů System center.

   - `Rights`: Zarovná vybrané ovládací prvky jejich pravé straně.

   - `Tops`: Zarovná vybrané ovládací prvky jeho horní hrany.

   - `Middles`: Zarovná vybrané ovládací prvky svisle podél jejich střední body.

   - `Bottoms`: Zarovná vybrané ovládací prvky dolního okraje.

## <a name="to-even-the-spacing-between-controls"></a>Dodavatelské mezer mezi ovládacími prvky

**Dialogové okno** editor umožňuje ovládacích prvků místo rovnoměrně mezi nejkrajnější vybraných ovládacích prvků.

1. Vyberte ovládací prvky, které chcete změnit uspořádání.

1. Z **formátu** nabídce zvolte **místo rovnoměrně**a pak vyberte jednu z následujících zarovnání mezery:

   - `Across`: místo ovládacích prvků rovnoměrně mezi první a poslední ovládací prvek.

   - `Down`: místo ovládacích prvků rovnoměrně mezi horní a nejspodnějších ovládací prvek.

## <a name="to-center-controls-in-a-dialog-box"></a>Zarovnat na střed ovládacích prvků v dialogovém okně

1. Vyberte ovládací prvek nebo prvky, které chcete změnit uspořádání.

1. Z **formátu** nabídce zvolte **Center v dialogovém okně**a pak vyberte jednu z následujících opatření:

   - `Vertical`: střed ovládacích prvků v dialogovém okně svisle.

   - `Horizontal`: střed ovládacích prvků v dialogovém okně vodorovně.

## <a name="to-arrange-push-buttons-along-the-right-or-bottom-of-a-dialog-box"></a>Uspořádání tlačítek podél pravé nebo dolní části dialogového okna

1. Vyberte jeden nebo více tlačítek.

1. Z **formátu** nabídce zvolte **uspořádat tlačítka**a pak vyberte jednu z následujících opatření:

   - `Right`: zarovná tlačítek podél pravého okraje dialogového okna.

   - `Bottom`: zarovná tlačítek podél dolního okraje dialogového okna.

       Pokud vyberete ovládací prvek než příkazové tlačítko, jeho pozice nemá vliv.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Uspořádání ovládacích prvků v dialogových oknech](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)