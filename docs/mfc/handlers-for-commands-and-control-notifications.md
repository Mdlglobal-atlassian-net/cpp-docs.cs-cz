---
title: Obslužné rutiny pro příkazy a oznámení ovládacích prvků
ms.date: 11/04/2016
helpviewer_keywords:
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
ms.openlocfilehash: 43b6a517b680a5f6ff092337fbf3d90dd0115dd7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907971"
---
# <a name="handlers-for-commands-and-control-notifications"></a>Obslužné rutiny pro příkazy a oznámení ovládacích prvků

Nejsou k dispozici žádné výchozí obslužné rutiny pro příkazy nebo zprávy s oznámením o řízení. Proto jste vázáni pouze podle konvence při pojmenovávání obslužných rutin pro tyto kategorie zpráv. Pokud namapujete oznámení příkazu nebo ovládacího prvku na obslužnou rutinu, [Průvodce třídou](reference/mfc-class-wizard.md) navrhne název na základě ID příkazu nebo kódu oznámení ovládacího prvku. Můžete přijmout navrhovaný název, změnit ho nebo ho nahradit.

Konvence navrhuje, aby obslužné rutiny názvů v obou kategoriích pro objekt uživatelského rozhraní, které představují. Proto může být obslužná rutina pro příkaz Vyjmout v nabídce Upravit pojmenována

[!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

Vzhledem k tomu, že příkaz Vyjmout je tak běžně implementován v aplikacích, rozhraní předdefinuje ID příkazu pro příkaz Vyjmout jako **ID_EDIT_CUT**. Seznam všech předdefinovaných ID příkazů najdete v souboru AFXRES. Y. Další informace najdete v tématu [standardní příkazy](../mfc/standard-commands.md).

Kromě toho konvence navrhne obslužnou rutinu pro zprávu oznámení **BN_CLICKED** z tlačítka označeného "moje tlačítko" může mít název

[!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

Tento příkaz můžete přiřadit ID **IDC_MY_BUTTON** , protože se jedná o ekvivalent objektu uživatelského rozhraní specifického pro aplikaci.

Obě kategorie zpráv nevyužívají žádné argumenty a nevrací žádnou hodnotu.

## <a name="see-also"></a>Viz také:

[Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)
