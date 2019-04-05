---
title: Testování vlastností a událostí pomocí testovacího kontejneru
ms.date: 11/04/2016
helpviewer_keywords:
- testing, test containers
- tstcon32.exe
- debugging ActiveX controls
- test container
- ActiveX Control Test Container
- ActiveX controls [MFC], testing
- properties [MFC], testing
ms.assetid: 626867cf-fe53-4c30-8973-55bb93ef3917
ms.openlocfilehash: 977ef29095e652ab40028a2e8ba7feffabf56418
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781065"
---
# <a name="testing-properties-and-events-with-test-container"></a>Testování vlastností a událostí pomocí testovacího kontejneru

Aplikace typu kontejner testu, dodávané v jazyce Visual C++ je kontejner ovládacího prvku ActiveX pro účely testování a ladění ovládacích prvků ActiveX. Kontejner testů umožňuje vývojářům ovládacího prvku k otestování funkce ovládacího prvku tak, že změníte jeho vlastnosti, volání metody a vyvolání jeho událostí. Kontejner testu můžete zobrazit protokoly oznámení pro vázání dat a také poskytuje funkce pro testování funkce trvalosti ovládacího prvku ActiveX: vlastnosti uložit do datového proudu nebo podúložiště, načítat je znovu a prozkoumejte data uložená datového proudu. Tato část popisuje, jak používat základní funkce kontejner testu. Další informace, vyberte **pomáhají** nabídky při spuštění kontejneru testů.

### <a name="to-access-the-activex-control-test-container"></a>Pro přístup k kontejner testů ovládacích prvků ActiveX

1. Sestavení [lze kontejner TSTCON vzorku: Kontejner testů ovládacích prvků ActiveX](../overview/visual-cpp-samples.md).

### <a name="to-test-your-activex-control"></a>Testování ovládacího prvku ActiveX

1. Na **upravit** nabídky kontejner testu, klikněte na tlačítko **vložte nový ovládací prvek**.

1. V **vložit ovládací prvek** pole, vyberte požadovaný prvek a klikněte na tlačítko **OK**. Ovládací prvek se zobrazí v kontejneru ovládacího prvku.

    > [!NOTE]
    >  Pokud váš ovládací prvek není uvedené v **vložit ovládací prvek** dialogové okno pole, ujistěte se, že jste ho zaregistrovali **registrovat ovládací prvky** z **souboru** nabídky testu Kontejner.

V tomto okamžiku můžete otestovat, vlastnosti nebo události ovládacího prvku.

#### <a name="to-test-properties"></a>K otestování vlastnosti

1. Na **ovládací prvek** nabídky, klikněte na tlačítko **vyvolání metody**.

1. V **název metody** rozevíracího seznamu vyberte metodu PropPut pro vlastnost, kterou potřebujete otestovat.

1. Upravit **hodnota parametru** nebo **typ parametru** a klikněte na **nastavit hodnotu** tlačítko.

1. Klikněte na tlačítko **Invoke** použít novou hodnotu do objektu.

   Vlastnost nyní obsahuje novou hodnotu.

#### <a name="to-test-events-and-specify-the-destination-of-event-information"></a>Testovat události a zadejte cílovou složku informací o události.

1. Na **možnosti** nabídky, klikněte na tlačítko **protokolování**.

1. Zadejte cílovou složku z informací o události.

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[Postupy: Ladění ovládacího prvku ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)
