---
title: Definování obslužné rutiny zpráv pro zrcadlené zprávy
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: f7f90d3347ac61abcfcb48e77ef39aa2626ae5c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365856"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Definování obslužné rutiny zpráv pro zrcadlené zprávy

Po vytvoření nové třídy řízení knihovny MFC můžete definovat obslužné rutiny zpráv pro něj. Obslužné rutiny zpráv umožňují třídu ovládacího prvku zpracovávat vlastní zprávy před přijetím zprávy nadřazenou zprávou. Funkci [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) můžete použít k odesílání zpráv z ovládacího prvku do nadřazeného okna.

Pomocí této funkce můžete například vytvořit seznam, který se překreslí sám, místo aby se spoléhal na nadřazené okno (byl nakreslen vlastník). Další informace o odražených zprávách naleznete v [tématu Zpracování odražených zpráv](../../mfc/handling-reflected-messages.md).

Chcete-li vytvořit [ovládací prvek ActiveX](../../mfc/activex-controls-on-the-internet.md) se stejnou funkcí, je nutné vytvořit projekt ovládacího prvku ActiveX.

> [!NOTE]
> Nelze přidat odraženou zprávu (OCM_*zpráva)* pro ovládací prvek ActiveX pomocí Průvodce třídou, jak je popsáno níže. Tyto zprávy je nutné přidat ručně.

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>Definování obslužné rutiny zprávy pro odraženou zprávu z Průvodce třídou

1. Přidejte ovládací prvek, například seznam, ovládací prvek výztuže, panel nástrojů nebo ovládací prvek stromu, do projektu knihovny MFC.

1. V zobrazení třídklikněte na název třídy ovládacího prvku.

1. V [Průvodci třídou](mfc-class-wizard.md)se název třídy ovládacího prvku zobrazí v seznamu **Název třídy.**

1. Kliknutím na kartu **Zprávy** zobrazte dostupné zprávy systému Windows, které chcete přidat do ovládacího prvku.

1. Vyberte odraženou zprávu, pro kterou chcete definovat obslužnou rutinu. Odražené zprávy jsou označeny rovnítkem (=).

1. Klepnutím na buňku v pravém sloupci průvodcem pro třídu \<zobrazíte navrhovaný název obslužné rutiny jako přidání>*HandlerName*. (Například **=WM_CTLCOLOR** zpráva obslužná rutina navrhuje \<přidat>**CtlColor**).

1. Klikněte na navrhovaný název, který chcete přijmout. Obslužná rutina je přidána do projektu.

1. Chcete-li upravit nebo odstranit obslužnou rutinu zprávy, opakujte kroky 4 až 7. Chcete-li upravit nebo odstranit, klepněte na buňku obsahující název obslužné rutiny a klepněte na příslušnou úlohu.

## <a name="see-also"></a>Viz také

[Mapování zpráv na funkce](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepsání virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Obslužná rutina zprávy knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigace ve struktuře třídy](../../ide/navigate-code-cpp.md)
