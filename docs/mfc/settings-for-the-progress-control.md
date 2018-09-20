---
title: Nastavení pro ovládací prvek průběh | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6b11189e3e0a8381ade372841e6c7b25a5a9fa0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434632"
---
# <a name="settings-for-the-progress-control"></a>Nastavení pro ovládací prvek průběh

Základní nastavení pro ovládací prvek průběh ([atributu CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) jsou rozsahu a aktuální pozici. Rozsah představuje celou dobu trvání operace. Aktuální pozice představuje pokroku, který vaše aplikace odeslala směrem k dokončení operace. Všechny změny oblast nebo umístění způsobit, že ovládací prvek průběh svoje vlastní překreslení.

Ve výchozím nastavení, je nastaven rozsah 0 - 100 a počáteční pozice je nastavena na hodnotu 0. Chcete-li načíst aktuální nastavení rozsahu pro ovládací prvek průběh, použijte [getrange –](../mfc/reference/cprogressctrl-class.md#getrange) členskou funkci. Chcete-li změnit rozsah, použijte [SetRange](../mfc/reference/cprogressctrl-class.md#setrange) členskou funkci.

Nastavit pozici, použijte [SetPos](../mfc/reference/cprogressctrl-class.md#setpos). Pokud chcete načíst aktuální pozici bez zadání nové hodnoty, použijte [GetPos](../mfc/reference/cprogressctrl-class.md#getpos). Můžete například chtít jednoduše dotazování na stav aktuální operace.

Chcete-li aktuální pozici ovládacím prvkem průběh, použijte [StepIt](../mfc/reference/cprogressctrl-class.md#stepit). Chcete-li nastavit dobu, každý krok, použijte [SetStep](../mfc/reference/cprogressctrl-class.md#setstep)

## <a name="see-also"></a>Viz také

[Používání atributu CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

