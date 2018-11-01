---
title: Testování dialogového okna (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
ms.openlocfilehash: 101a2b556b2593953bfa6482f96d5b1aadc38d1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625062"
---
# <a name="testing-a-dialog-box-c"></a>Testování dialogového okna (C++)

Při návrhu dialogového okna můžete simulovat a testovat jeho chování za běhu bez kompilace programu. V tomto režimu můžete:

- Zadejte text, vyberte ze seznamu pole se seznamem, zapnout nebo vypnout možnosti a volit příkazy.

- Otestujte pořadí ovládacích prvků.

- Otestujte seskupení ovládacích prvků, jako jsou přepínače a zaškrtávací políčka.

- Otestujte klávesové zkratky pro ovládací prvky v dialogovém okně.

   > [!NOTE]
   > Připojení ke kódu dialogového okna pomocí průvodců nejsou zahrnuta v simulaci.

Při testování dialogového okna se obvykle zobrazuje v umístění, které jsou relativní vůči hlavnímu oknu programu. Pokud jste nastavili v dialogovém okně **absolutní zarovnání** vlastnost **True**, zobrazí se dialogové okno v pozici, která je relativní vzhledem k levého horního rohu obrazovky.

### <a name="to-test-a-dialog-box"></a>Testování dialogového okna

1. Když **dialogové okno** editor není aktivní okno na řádku nabídek, zvolte **formátu** > **testovací dialogové okno**.

2. Chcete-li simulaci ukončit, stiskněte **Esc**, nebo prostě vybrat **Zavřít** tlačítka v dialogových oken, které testujete.

Informace o tom, jak přidat prostředky do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Editor dialogových oken](../windows/dialog-editor.md)<br/>
[Zobrazení nebo skrytí panelu nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)