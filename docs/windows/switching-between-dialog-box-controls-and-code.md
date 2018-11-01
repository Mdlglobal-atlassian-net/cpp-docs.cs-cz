---
title: Přepínání mezi ovládacími prvky pole (C++) dialogové okno a kódem
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog Editor [C++], accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog Editor [C++], switching between controls and code
ms.assetid: 7da73815-b853-4203-ba45-bbe570695122
ms.openlocfilehash: 4d48386e93fcea6d30fee6c57c288944bbd8d9ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644298"
---
# <a name="switching-between-dialog-box-c-controls-and-code"></a>Přepínání mezi ovládacími prvky pole (C++) dialogové okno a kódem

V aplikacích MFC můžete dvakrát kliknout na dialogové okno Ovládací prvky pro přechod na svůj kód obslužné rutiny nebo k rychlému vytvoření zástupné procedury funkcí obslužných rutin.

Ovládací prvek vybraný, klikněte **ControlEvents** tlačítko nebo **zprávy** tlačítko [okno vlastností](/visualstudio/ide/reference/properties-window) Chcete-li zobrazit úplný seznam událostí a zpráv Windows k dispozici pro vybranou položku. Zvolte ze seznamu a vytvořit nebo upravit funkce obslužné rutiny.

### <a name="to-jump-to-code-from-the-dialog-editor"></a>Můžete přejít ke kódu z editoru dialogových oken

1. Dvakrát klikněte na ovládací prvek v dialogovém okně můžete přejít k deklaraci jeho naposledy implementované zprávy funkci pro zpracování. (Pro třídy založený na knihovně ATL dialogových oken, můžete vždy přejít na definici konstruktoru.)

### <a name="to-view-events-for-a-control"></a>Chcete-li zobrazit události pro ovládací prvek

1. Ovládací prvek vybraný, klikněte **ControlEvents** tlačítko [okno vlastností](/visualstudio/ide/reference/properties-window).

   > [!NOTE]
   > Kliknutím **ControlEvents** tlačítko, kdy *dialogové okno* má fokus zpřístupňuje seznam všech ovládacích prvků v poli dialogové okno, které můžete rozbalit Úprava události pro jednotlivé ovládací prvky.

   Pokud jeden ovládací prvek má fokus v dialogovém okně, pravým tlačítkem myši a vybrat můžete **přidat obslužnou rutinu události** z místní nabídky. To umožňuje zadat třídu, ke kterému je přidání obslužné rutiny. Další informace najdete v tématu [přidání obslužné rutiny události](../ide/adding-an-event-handler-visual-cpp.md).

### <a name="to-view-messages-for-a-dialog-box"></a>Chcete-li zobrazit zprávy pro dialogové okno

1. Vybrané dialogovém okně klikněte **zprávy** tlačítko [okno vlastností](/visualstudio/ide/reference/properties-window).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor dialogových oken](../windows/dialog-editor.md)