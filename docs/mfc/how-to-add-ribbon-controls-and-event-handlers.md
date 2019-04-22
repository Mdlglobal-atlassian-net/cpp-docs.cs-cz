---
title: 'Postupy: Přidání ovládacích prvků pásu karet a obslužných rutin událostí'
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: c21e8b86962ebf37ca1a06bae056d09b9a9dbb2f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58770120"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>Postupy: Přidání ovládacích prvků pásu karet a obslužných rutin událostí

Ovládací prvky pásu karet jsou prvky, jako jsou tlačítka a polí se seznamem, které přidáte do panelů. Panely jsou oblasti na pásu karet, které zobrazují skupina souvisejících ovládacích prvků.

V tomto tématu otevřete Návrhář pásu karet, přidejte tlačítko a propojit událost, která se zobrazí "Hello World".

### <a name="to-open-the-ribbon-designer"></a>Chcete-li otevřít Návrhář pásu karet

1. V sadě Visual Studio na **zobrazení** nabídky, klikněte na tlačítko **zobrazení prostředků**.

1. V **zobrazení prostředků**, dvakrát klikněte na prostředek pásu karet se zobrazí na návrhové ploše.

### <a name="to-add-a-button-and-an-event-handler"></a>Chcete-li přidat tlačítko a obslužné rutiny události

1. Z **nástrojů**, klikněte na tlačítko **tlačítko** a přetáhněte ji na panelu v návrhové ploše.

1. Klikněte pravým tlačítkem na tlačítko a klikněte na tlačítko **přidat obslužnou rutinu události**.

1. V **Průvodce obslužnou rutinou události**potvrďte výchozí nastavení a klikněte na tlačítko **přidávat a upravovat**. Další informace najdete v tématu [Průvodce obslužnou rutinou události](../ide/event-handler-wizard.md).

1. V editoru kódu přidejte následující kód do obslužné rutiny:

```
    MessageBox((LPCTSTR)L"Hello World");
```

## <a name="see-also"></a>Viz také:

[Vzorek RibbonGadgets: Aplikace pro miniaplikace na pásu karet](../overview/visual-cpp-samples.md)<br/>
[Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md)
