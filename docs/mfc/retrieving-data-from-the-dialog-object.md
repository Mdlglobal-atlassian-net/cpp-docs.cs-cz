---
title: Načítání dat z objektu dialogového okna
ms.date: 11/04/2016
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
ms.openlocfilehash: 903d76a1e672d05a3c093e528f7153562df8e3e5
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685578"
---
# <a name="retrieving-data-from-the-dialog-object"></a>Načítání dat z objektu dialogového okna

Rozhraní poskytuje snadný způsob, jak inicializovat hodnoty ovládacích prvků v dialogovém okně a načíst hodnoty z ovládacích prvků. Pracné ručním přístupem je volání funkcí, jako jsou členské funkce `SetDlgItemText` a `GetDlgItemText` třídy `CWnd`, které se vztahují k ovládacím prvkům Windows. S těmito funkcemi získáte přístup ke každému ovládacímu prvku jednotlivě pro nastavení nebo získání jeho hodnoty, volání funkcí, jako je například `SetWindowText` a `GetWindowText`. Přístup k rozhraní se automatizuje inicializací i načítáním.

Výměna dialogových dat (DDX) umožňuje snadněji vyměňovat data mezi ovládacími prvky v dialogovém okně a členskými proměnnými v objektu dialogového okna. Tato výměna funguje jak oběma způsoby. Chcete-li inicializovat ovládací prvky v dialogovém okně, můžete nastavit hodnoty datových členů v objektu dialogového okna a rozhraní přenese hodnoty do ovládacích prvků před zobrazením dialogového okna. Pak můžete kdykoli aktualizovat datové členy dialogových oken daty zadanými uživatelem. V tomto okamžiku můžete použít data odkazem na proměnné datových členů.

Můžete také zajistit, aby byly hodnoty ovládacích prvků dialog ověřovány automaticky pomocí ověřování dat dialogového okna (DDV).

DDX a DDV jsou podrobněji vysvětleny v tématu [Výměna a ověřování dat dialogových oken](../mfc/dialog-data-exchange-and-validation.md).

V případě modálního dialogového okna můžete načíst všechna data, která uživatel zadal, když `DoModal` vrátí IDOK, ale před zničením objektu dialogového okna. Pro nemodální dialogové okno můžete načíst data z objektu dialogového okna kdykoli voláním `UpdateData` s argumentem **true** a následným přístupem k proměnným členů třídy dialogového okna. Tento předmět je podrobněji popsán v tématu [Výměna a ověřování dat dialogových oken](../mfc/dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Další informace najdete v tématech

[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)
