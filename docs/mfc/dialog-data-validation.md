---
title: Ověřování dat dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- validating data [MFC], message boxes
- data validation [MFC], dialog boxes
- dialog boxes [MFC], validating data
- validating data [MFC], dialog box data entry
- DDV (dialog data validation) [MFC]
- data validation [MFC], message boxes
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
ms.openlocfilehash: c89ed82b148062ddb64fa85eaabda12f44e59895
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685761"
---
# <a name="dialog-data-validation"></a>Ověřování dat dialogového okna

Ověřování můžete kromě výměny dat zadat také voláním funkce DDV, jak je znázorněno v příkladu v části [Výměna dat dialogových oken](../mfc/dialog-data-exchange.md). Volání `DDV_MaxChars` v příkladu ověřuje, že řetězec zadaný v ovládacím prvku textové pole není delší než 20 znaků. Funkce DDV obvykle upozorní uživatele na okno se zprávou, pokud se ověření nepovede a umístí fokus na problematické řízení, aby uživatel mohl znovu zadat data. Funkce DDV pro daný ovládací prvek musí být volána ihned po funkci DDX pro stejný ovládací prvek.

Můžete také definovat vlastní rutiny DDX a DDV. Podrobnosti o tomto a dalších aspektech DDX a DDV naleznete v tématu [technická Poznámka (MFC) 26](../mfc/tn026-ddx-and-ddv-routines.md).

[Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md) zapíše všechna volání DDX a DDV v datové mapě za vás.

## <a name="see-also"></a>Další informace najdete v tématech

[Výměna a ověřování dat dialogových oken](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Výměna dat dialogových oken](../mfc/dialog-data-exchange.md)
