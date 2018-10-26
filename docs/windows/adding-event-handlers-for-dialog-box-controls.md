---
title: Přidání obslužných rutin události pro ovládací prvky dialogového okna pole (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog Editor [C++], adding event handlers to controls
- controls [C++], event handlers
- dialog box controls [C++], events
- event handlers, for dialog box controls
ms.assetid: f9c70f24-ea6f-44df-82eb-78a2deaee769
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ebb644c64bbc5eba65860ffb1c1115bfc7662951
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075266"
---
# <a name="adding-event-handlers-for-dialog-box-controls-c"></a>Přidání obslužných rutin události pro ovládací prvky dialogového okna pole (C++)

Pro projekt dialogová okna, které už jsou spojeny s třídou můžete využít výhod některé klávesové zkratky, při vytváření obslužných rutin událostí. Můžete rychle vytvořit obslužnou rutinu pro událost oznámení výchozí ovládací prvek nebo pro všechny příslušné zprávy Windows.

### <a name="to-create-a-handler-for-the-default-control-notification-event"></a>Chcete-li vytvořit obslužnou rutinu pro událost oznámení výchozí ovládací prvek

1. Poklepejte na ovládací prvek. **Text** se otevře editor.

2. Přidat kód obslužné rutiny pro ovládací prvek oznámení **Text** editoru.

### <a name="to-create-a-handler-for-any-applicable-windows-message"></a>Chcete-li vytvořit obslužnou rutinu pro všechny příslušné zprávy Windows

1. Klepněte na ovládací prvek, pro kterou chcete zpracovat událost oznámení.

2. V [okno vlastností](/visualstudio/ide/reference/properties-window), klikněte na tlačítko **ControlEvents** tlačítko a zobrazte seznam nejčastějších událostí Windows přidružený k ovládacímu prvku. Například standardní **OK** tlačítko **o** dialogové okno obsahuje následující události oznámení:

   - BN_CLICKED

   - BN_DOUBLECLICKED

   - BN_KILLFOCUS

   - BN_SETFOCUS

   > [!NOTE]
   > Můžete také vybrat dialogových oken a klikněte na tlačítko **ControlEvents** tlačítko a zobrazte seznam obvyklých událostí Windows pro všechny ovládací prvky v dialogovém okně.

3. V **vlastnosti** okna, klikněte na tlačítko v pravém sloupci vedle událostí ke zpracování a pak vyberte název události navrhované oznámení (například `OnBnClickedOK` zpracovává BN_CLICKED).

   > [!NOTE]
   > Alternativně můžete zadat název obslužné rutiny události podle vašeho výběru, namísto výběru výchozí název obslužné rutiny události.

   Po výběru události Visual Studio otevře **textový Editor** a zobrazí kód obslužné rutiny události. Například následující kód se přidá výchozí `OnBnClickedOK`:

    ```cpp
    void CAboutDlg::OnBnClickedOk(void)
    {
        // TODO: Add your control notification handler code here
    }
    ```

Pokud chcete přidat obslužnou rutinu události pro třídu jiné než jedna implementace dialogových oken, použijte [Průvodce obslužnou rutinou události](../ide/event-handler-wizard.md). Další informace najdete v tématu [přidání obslužné rutiny události](../ide/adding-an-event-handler-visual-cpp.md).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Výchozí události ovládacích prvků](../windows/default-control-events.md)<br/>
[Definování členských proměnných pro ovládací prvky dialogového okna](../windows/defining-member-variables-for-dialog-controls.md)<br/>
[Ovládací prvky dialogových oken a typy proměnných](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Přidání třídy](../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepisování virtuální funkce](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Popisovače zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md)