---
title: Navrhování dialogové okno (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
ms.openlocfilehash: 4a879f6bb1cdcd4b4897e510fb21d04500dfd3f2
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742684"
---
# <a name="designing-a-dialog-box-c"></a>Navrhování dialogové okno (C++)

Umístění a velikosti dialogového okna C++ a umístění a velikost ovládacích prvků na ní, se měří v jednotkách dialogového okna. Hodnoty jednotlivých ovládacích prvků a dialogové okno se zobrazí v pravém dolním rohu sady Visual Studio se na stavovém řádku při výběru.

Při návrhu dialogového okna, můžete také simulovat a testovat jeho chování za běhu bez kompilace programu. V tomto režimu můžete:

- Zadejte text, vyberte ze seznamu pole se seznamem, zapnout nebo vypnout možnosti a volit příkazy.

- Otestujte pořadí ovládacích prvků.

- Otestujte seskupení ovládacích prvků, jako jsou přepínače a zaškrtávací políčka.

- Otestujte klávesové zkratky pro ovládací prvky v dialogovém okně.

   > [!NOTE]
   > Připojení ke kódu dialogového okna pomocí průvodců nejsou zahrnuta v simulaci.

Při testování dialogového okna se obvykle zobrazuje v umístění, které jsou relativní vůči hlavnímu oknu programu. Pokud jste nastavili v dialogovém okně **absolutní zarovnání** vlastnost **True**, zobrazí se dialogové okno v pozici, která je relativní vzhledem k levého horního rohu obrazovky.

Informace o tom, jak přidat prostředky do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index).

## <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>K určení umístění a velikosti dialogového okna

Existují tři vlastnosti, které můžete nastavit [okno vlastností](/visualstudio/ide/reference/properties-window) k určení, kde se zobrazí dialogové okno na obrazovce. **Center** vlastnost je logická hodnota, pokud hodnotu nastavíte na **True**, dialogové okno se vždy zobrazí ve středu obrazovky. Pokud ji nastavíte na **False**, pak můžete nastavit **Pozice_x** a **Pozice_y** explicitně definované tam, kde na obrazovce se zobrazí dialogové okno Vlastnosti. Jsou vlastnosti pozici posunutí hodnoty v levém horním rohu oblasti zobrazení, která je definována jako `{X=0, Y=0}`. Pozice je taky založený na **absolutní zarovnání** vlastnost: Pokud **True**, souřadnice jsou relativní vzhledem k obrazovce; Pokud **False**, souřadnice jsou relativní vzhledem k dialogového okna okno vlastníka.

## <a name="to-test-a-dialog-box"></a>Testování dialogového okna

1. Když **dialogové okno** editor není aktivní okno na řádku nabídek, zvolte **formátu** > **testovací dialogové okno**.

1. Chcete-li simulaci ukončit, stiskněte **Esc**, nebo prostě vybrat **Zavřít** tlačítko v dialogovém okně, kterou testujete.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Editor dialogových oken](../windows/dialog-editor.md)<br/>
[Zobrazení nebo skrytí panelu nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)