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
ms.openlocfilehash: cef9941cccd49ca61f0a93472636656f7241a61e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383812"
---
# <a name="dialog-data-validation"></a>Ověřování dat dialogového okna

Ověření kromě výměny dat můžete určit pomocí volání funkce DDV, jak je znázorněno v příkladu v [výměna dat dialogových oken](../mfc/dialog-data-exchange.md). `DDV_MaxChars` Volání v příkladu ověřuje, že řetězec zadaný v ovládacím prvku textového pole není delší než 20 znaků. Funkce DDV obvykle upozorní uživatele s okno se zprávou, pokud ověření selže a umístí na problematický ovládací prvek fokus, takže uživatel může znovu data. DDV funkce pro daný ovládací prvek musí být volána bezprostředně po funkci DDX pro stejný ovládací prvek.

Můžete také definovat vlastní vlastní rutiny DDX a DDV. Podrobnosti o tomto a dalších aspektů DDX a DDV najdete v tématu [26 Technická poznámka MFC](../mfc/tn026-ddx-and-ddv-routines.md).

[Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md) bude zapisovat všechny DDX a DDV volá v objektu map data za vás.

## <a name="see-also"></a>Viz také:

[Výměna a ověřování dat dialogových oken](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Výměna dat dialogových oken](../mfc/dialog-data-exchange.md)
