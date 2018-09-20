---
title: 'Postupy: Přidání ovládacích prvků pásu karet a obslužných rutin událostí | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3c4af695553bc97815915454bda2aae481543e9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427950"
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

## <a name="see-also"></a>Viz také

[Vzorek RibbonGadgets: Aplikace pro miniaplikace na pásu karet](../visual-cpp-samples.md)<br/>
[Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md)

