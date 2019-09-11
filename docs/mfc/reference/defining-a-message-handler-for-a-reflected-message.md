---
title: Definování obslužné rutiny zpráv pro zrcadlené zprávy
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: 1e38c63464cacf445688a1d431a65af21eac86f4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907930"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Definování obslužné rutiny zpráv pro zrcadlené zprávy

Jakmile vytvoříte novou třídu ovládacího prvku MFC, můžete pro ni definovat obslužné rutiny zpráv. Zrcadlené obslužné rutiny zpráv umožňují vaší třídě ovládacího prvku zpracovávat vlastní zprávy před přijetím zprávy nadřazeným objektem. Pomocí funkce MFC [CWnd:: SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) můžete odesílat zprávy z ovládacího prvku do nadřazeného okna.

Díky této funkci můžete například vytvořit seznam, který se znovu nakreslí, ale nespoléhat se na nadřazené okno, aby to provedl (nakreslený vlastník). Další informace o zrcadlených zprávách najdete v tématu [zpracování zrcadlených zpráv](../../mfc/handling-reflected-messages.md).

Chcete-li vytvořit [ovládací prvek ActiveX](../../mfc/activex-controls-on-the-internet.md) se stejnými funkcemi, je nutné vytvořit projekt pro ovládací prvek ActiveX.

> [!NOTE]
>  Nelze přidat zrcadlenou zprávu (OCM_*zpráva*) pro ovládací prvek ActiveX pomocí Průvodce třídou, jak je popsáno níže. Tyto zprávy je nutné přidat ručně.

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>Definování obslužné rutiny zpráv pro zrcadlenou zprávu z Průvodce třídou

1. Do projektu knihovny MFC přidejte ovládací prvek, jako je například seznam, ovládací prvek matrice, panel nástrojů nebo ovládací prvek stromu.

1. V Zobrazení tříd klikněte na název vaší třídy ovládacího prvku.

1. V [Průvodci třídou](mfc-class-wizard.md)se název třídy ovládacího prvku zobrazí v seznamu **název třídy** .

1. Kliknutím na kartu **zprávy** zobrazíte zprávy systému Windows, které jsou k dispozici pro přidání do ovládacího prvku.

1. Vyberte zrcadlenou zprávu, pro kterou chcete definovat obslužnou rutinu. Odražené zprávy jsou označeny symbolem rovná se (=).

1. Kliknutím na buňku v pravém sloupci v průvodci třída zobrazíte navrhovaný název obslužné rutiny jako \<Add >*Handler*. (Například obslužná rutina zprávy **= WM_CTLCOLOR** navrhuje \<přidat >**CTLCOLOR**).

1. Klikněte na navrhovaný název, který chcete přijmout. Obslužná rutina se přidá do vašeho projektu.

1. Chcete-li upravit nebo odstranit obslužnou rutinu zprávy, opakujte kroky 4 až 7. Kliknutím na buňku, která obsahuje název obslužné rutiny, můžete upravit nebo odstranit a kliknout na příslušnou úlohu.

## <a name="see-also"></a>Viz také:

[Mapování zpráv na funkce](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepsání virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Obslužná rutina zpráv MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigace ve struktuře třídy](../../ide/navigate-code-cpp.md)
