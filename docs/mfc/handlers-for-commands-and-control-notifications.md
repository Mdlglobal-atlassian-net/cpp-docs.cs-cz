---
title: Obslužné rutiny pro příkazy a oznámení ovládacích prvků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bda42393cd55b60ab787665b51957bb2f94c5df3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430072"
---
# <a name="handlers-for-commands-and-control-notifications"></a>Obslužné rutiny pro příkazy a oznámení ovládacích prvků

Neexistují žádné výchozí obslužné rutiny pro příkazy nebo zpráv s oznámením ovládacího prvku. Proto určitě pouze podle konvence názvů vaší obslužné rutiny pro tyto kategorie zpráv. Při namapování oznámení příkazu nebo řízení na obslužnou rutinu okna vlastností navrhne název založený na kódu v příkazu ID nebo oznámení ovládacího prvku. Můžete přijmout navržený název, změňte ji nebo ji nahradit.

Konvence navrhne název obslužné rutiny v obou kategoriích pro objekt uživatelského rozhraní, které reprezentují. Proto může mít název obslužnou rutinu pro příkaz Cut v nabídce Úpravy

[!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

Protože příkaz Cut je proto obvykle implementovány v aplikacích, rozhraní predefines ID příkazu pro příkaz Cut jako **id_edit_cut –**. Seznam všech přednastaveného příkazu ID naleznete v souboru AFXRES. H. Další informace najdete v tématu [standardní příkazy](../mfc/standard-commands.md).

Kromě toho konvence navrhuje obslužnou rutinu pro **BN_CLICKED** zprávy oznámení pomocí tlačítka s popiskem "My Button" může mít název.

[!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

Tento příkaz může přiřadit ID **IDC_MY_BUTTON** vzhledem k tomu, že je ekvivalentní objekt uživatelského rozhraní specifické pro aplikaci.

Obě kategorie zpráv, které nepřebírají žádné argumenty a vracet žádnou hodnotu.

## <a name="see-also"></a>Viz také

[Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)
