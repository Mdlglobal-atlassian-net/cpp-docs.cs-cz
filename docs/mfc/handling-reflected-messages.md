---
title: Zpracování reflektovaných zpráv
ms.date: 11/04/2016
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
ms.openlocfilehash: 973e8cff24eca37b1806207d081636f0d1b38365
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240558"
---
# <a name="handling-reflected-messages"></a>Zpracování reflektovaných zpráv

Zpráva reflexe umožňuje zpracovávat zprávy pro ovládací prvek, jako například **WM_CTLCOLOR –**, **wm_command –**, a **WM_NOTIFY**, v rámci samotného ovládacího prvku. Samostatná, přenosná díky tomu ovládacího prvku. Mechanismu, který funguje s běžných ovládacích prvků Windows i s ovládacími prvky ActiveX (dříve se označovaly jako ovládací prvky OLE).

Zpráva reflexe umožňuje znovu použít vaše `CWnd`-snadněji odvozené třídy. Zpráva reflexe pracuje prostřednictvím [CWnd::OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify), pomocí speciální **ON_XXX_REFLECT** zprávy položek mapování: například **ON_CTLCOLOR_REFLECT** a **ON_CONTROL_REFLECT**. [Technická poznámka 62](../mfc/tn062-message-reflection-for-windows-controls.md) vysvětluje reflexe zprávy podrobněji.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat

- [Další informace o reflexe zprávy](../mfc/tn062-message-reflection-for-windows-controls.md)

- [Implementace reflexe zprávy pro běžný ovládací prvek](../mfc/tn062-message-reflection-for-windows-controls.md)

- [Implementace reflexe zprávy pro ovládací prvek ActiveX](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>Viz také:

[Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)
