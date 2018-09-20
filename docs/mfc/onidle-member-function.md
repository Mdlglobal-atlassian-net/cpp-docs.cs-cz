---
title: ONIDLE – členská funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OnIdle
dev_langs:
- C++
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b334a4561af40b69bc367ab5b1129afa8fb29ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377291"
---
# <a name="onidle-member-function"></a>OnIdle – členská funkce

Při zpracování zprávy bez Windows se volá framework [CWinApp](../mfc/reference/cwinapp-class.md) členskou funkci [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (podle Reference knihovny MFC).

Přepsat `OnIdle` k provedení úlohy na pozadí. Výchozí verze aktualizace stavu objektů uživatelského rozhraní, jako jsou tlačítka na panelu nástrojů a provádí vyčištění dočasné objekty vytvořené v rámci rozhraní tím jeho operace. Následující obrázek znázorňuje, jakým způsobem volá smyčky zpráv `OnIdle` při nejsou žádné zprávy ve frontě.

![Proces smyčky zpráv](../mfc/media/vc387c1.gif "vc387c1") The smyčky zpráv

Další informace o tom, co můžete učinit nečinné smyčky, naleznete v tématu [zpracování nečinné smyčky](../mfc/idle-loop-processing.md).

## <a name="see-also"></a>Viz také

[CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
