---
title: Načítání dat z objektu dialogového okna | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], retrieving user data
- dialog box data [MFC]
- data [MFC], retrieving
- GetDlgItemText method [MFC]
- SetDlgItemText method [MFC]
- SetWindowText method [MFC]
- dialog box data [MFC], retrieving
- retrieving data [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- dialog box controls [MFC], initializing values
- DDX (dialog data exchange) [MFC]
- MFC dialog boxes [MFC], retrieving user input
- data retrieval [MFC], dialog boxes
- data [MFC], dialog boxes
- DDX (dialog data exchange) [MFC], about DDX
- DDX (dialog data exchange) [MFC], retrieving data from Dialog object
- GetWindowText method [MFC]
ms.assetid: bdca2b61-6b53-4c2e-b426-8712c7a38ec0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3055468c04bba7c9cb999d0a642c0819524ff7e7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391407"
---
# <a name="retrieving-data-from-the-dialog-object"></a>Načítání dat z objektu dialogového okna

Rozhraní poskytuje snadný způsob inicializace hodnot ovládacích prvků v dialogovém okně a k načtení hodnot z ovládacích prvků. Více pracné ruční přístup je pro volání funkce, jako `SetDlgItemText` a `GetDlgItemText` členské funkce třídy `CWnd`, které platí pro ovládací prvek windows. Pomocí těchto funkcí je každý řízení přístupu jednotlivě a nastavit nebo získat její hodnota volání funkcí, jako `SetWindowText` a `GetWindowText`. Přístup v rámci automatizuje inicializace a načtení.

Výměna dat dialogových oken (DDX) umožňuje snadno vyměňovat data mezi ovládacími prvky v dialogovém okně proměnných pole a člen v objektu dialogového okna. Tato výměna pracuje oběma směry. Pokud chcete inicializovat ovládací prvky v dialogovém okně, můžete nastavit hodnoty datových členů v objektu dialogového okna a rozhraní bude přenos hodnoty k ovládacím prvkům předtím, než se zobrazí dialogové okno. Potom můžete kdykoli aktualizovat datové členy dialogové okno s daty zadané uživatelem. V tomto okamžiku můžete data ve odkazující na data členské proměnné.

Můžete také nastavit hodnoty ovládací prvky dialogového okna, chcete-li být ověřeny pomocí ověřování dat dialogového okna (DDV).

DDX a DDV jsou vysvětlené podrobněji [výměna dat dialogových oken a ověření](../mfc/dialog-data-exchange-and-validation.md).

Pro modální dialogové okno, můžete načíst žádná data, kdy uživatel zadal `DoModal` vrátí IDOK, ale před dialogové okno je objekt zničen. Pro nemodální dialogové okno, můžete načíst data z objektu dialogového okna kdykoli po zavolání `UpdateData` s argumentem **TRUE** a následný přístup k proměnné členů třídy dialogového okna. Tomuto tématu je popsáno podrobněji v [výměna dat dialogových oken a ověření](../mfc/dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Viz také

[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

