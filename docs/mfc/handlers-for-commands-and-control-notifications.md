---
title: Obslužné rutiny pro příkazy a oznámení ovládacích prvků | Microsoft Docs
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
ms.openlocfilehash: 7e6492c6ecc4c21c5c978ad031fed7182f2acee4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347230"
---
# <a name="handlers-for-commands-and-control-notifications"></a>Obslužné rutiny pro příkazy a oznámení ovládacích prvků
Neexistují žádné výchozí obslužné rutiny pro příkazy nebo zprávy oznámení ovládacího prvku. Proto jsou svázané pouze podle konvence v pojmenování vaší obslužné rutiny pro tyto kategorie zpráv. Při oznámení příkaz nebo ovládací prvek mapování na obslužnou rutinu, nabízí windows vlastnosti název založený na kód příkaz ID nebo oznámení ovládacího prvku. Můžete přijmout navrhovaný název, změnit nebo jej nahradit.  
  
 Konvence navrhuje, název obslužné rutiny v obou kategorie pro objekt uživatelského rozhraní, které reprezentují. Proto může být pojmenován obslužnou rutinu pro příkaz vyjmutí v nabídce Upravit  
  
 [!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]  
  
 Vzhledem k tomu, že příkaz Cut tak často implementace v aplikacích rozhraní predefines ID příkazu pro příkaz vyjmutí jako **id_edit_cut –**. Seznam všech přednastaveného příkazu ID naleznete v souboru AFXRES. H. Další informace najdete v tématu [standardní příkazy](../mfc/standard-commands.md).  
  
 Kromě toho konvence navrhuje obslužnou rutinu pro **BN_CLICKED** oznámení z tlačítko s názvem "Moje tlačítko" může mít název.  
  
 [!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]  
  
 Tento příkaz může přiřadit ID `IDC_MY_BUTTON` vzhledem k tomu, že je ekvivalentní objekt uživatelského rozhraní specifické pro aplikaci.  
  
 Obě kategorie zpráv nepřebírají žádné argumenty a vrátit žádná hodnota.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)
