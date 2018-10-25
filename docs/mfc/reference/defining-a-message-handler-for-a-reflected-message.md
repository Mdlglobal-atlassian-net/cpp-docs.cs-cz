---
title: Definování obslužné rutiny zpráv pro zrcadlené zprávy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.defining.msg.msghandler
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 104f9e0be67a350a1725dfbcd2bf234a8bc79553
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052561"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Definování obslužné rutiny zpráv pro zrcadlené zprávy

Po vytvoření nové třídě ovládacího prvku knihovny MFC můžete definovat obslužné rutiny zpráv pro něj. Obslužné rutiny reflektovaných zpráv povolit třídy vašeho ovládacího prvku pro zpracování vlastní zprávy před doručení zprávy nadřazenou položkou. Můžete používat knihovnu MFC [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) funkce pro odesílání zpráv z ovládacího prvku do nadřazeného okna.

Pomocí této funkce lze například vytvořit pole se seznamem, který bude svoje vlastní překreslení. spíše než spoléhání se na nadřazené okno provedete (vlastní vykreslování). Další informace o reflektované zprávy najdete v tématu [zpracování zprávy projeví](../../mfc/handling-reflected-messages.md).

Vytvoření [ovládacího prvku ActiveX](../../mfc/activex-controls-on-the-internet.md) pomocí stejné funkce, musíte vytvořit projekt pro ovládací prvek ActiveX.

> [!NOTE]
>  Nelze přidat reflektovaných zpráv (OCM_*zpráva*) pro prvek ActiveX řídit pomocí okna vlastnosti, jak je popsáno níže. Tyto zprávy musí přidat ručně.

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-properties-window"></a>Definování obslužné rutiny zpráv pro zrcadlené zprávy z okna Vlastnosti

1. Přidejte ovládací prvek, jako je například seznam, ovládacím prvkem matrice, panelu nástrojů nebo ovládací prvek stromu do projektu knihovny MFC.

1. V zobrazení tříd klikněte na název třídy vašeho ovládacího prvku.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), název třídy ovládacího prvku se zobrazí v **název třídy** seznamu.

1. Klikněte na tlačítko **zprávy** tlačítka pro zobrazení zpráv Windows k dispozici pro přidání do ovládacího prvku.

1. Přejděte dolů seznam zpráv v okně Vlastnosti, dokud se nezobrazí záhlaví **Reflected**. Kliknout **kategorie** tlačítko a sbalit zobrazení, abyste viděli **Reflected** záhlaví.

1. Vyberte zrcadlené zprávy, pro kterou chcete definovat obslužnou rutinu. Reflektované zprávy jsou označené rovnítko (=).

1. Klikněte na buňku v pravém sloupci v okně Vlastnosti, chcete-li zobrazit navrhovaný název obslužné rutiny jako \<Přidat >*HandlerName*. (Například **= WM_CTLCOLOR –** obslužná rutina zprávy navrhuje \<Přidat >**CtlColor**).

1. Klikněte na navrhovaný název tak, aby přijímal. Obslužná rutina se přidá do vašeho projektu.

   V pravém sloupci reflektované zprávy okna se zobrazí názvy obslužných rutin zpráv, které jste přidali.

9. Pokud chcete upravit nebo odstranit popisovač zpráv, opakujte kroky 4 až 7. Klikněte na buňku obsahující název obslužné rutiny na upravit nebo odstranit a klikněte na příslušnou úlohu.

## <a name="see-also"></a>Viz také

[Mapování zpráv na funkce](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepisování virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Popisovače zpráv knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigace strukturou třídy](../../ide/navigating-the-class-structure-visual-cpp.md)
