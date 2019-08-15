---
title: 'Automatizační servery: Problémy životního cyklu objektů'
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
ms.openlocfilehash: 74b4bf87b512d35c99942f4aa36174a8673079c5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509184"
---
# <a name="automation-servers-object-lifetime-issues"></a>Automatizační servery: Problémy životního cyklu objektů

Když klient služby Automation vytvoří nebo aktivuje položku OLE, server předá klienta ukazatel na tento objekt. Klient vytvoří odkaz na objekt prostřednictvím volání funkce OLE typu [IUnknown:: AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref). Tento odkaz je platný, dokud klient nevolá [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release). (Klientské aplikace napsané s třídami OLE knihovna Microsoft Foundation Class nemusí tato volání provést; rozhraní to udělá.) Systém OLE a samotný server mohou navázat odkazy na objekt. Server by neměl zničit objekt, pokud budou použity externí odkazy na objekt.

Rozhraní udržuje interní počet odkazů na libovolný objekt serveru odvozený z [CCmdTarget](../mfc/reference/ccmdtarget-class.md). Tento počet se aktualizuje, když klient automatizace nebo jiná entita přidá nebo uvolní odkaz na objekt.

Když se počet odkazů naplní na 0, rozhraní zavolá virtuální funkci [CCmdTarget:: OnFinalRelease](../mfc/reference/ccmdtarget-class.md#onfinalrelease). Výchozí implementace této funkce volá operátor **Delete** pro odstranění tohoto objektu.

Knihovna Microsoft Foundation Class poskytuje další možnosti pro řízení chování aplikace, když externí klienti mají odkazy na objekty aplikace. Kromě udržování počtu odkazů na jednotlivé objekty udržují servery globální počet aktivních objektů. Globální funkce [funkci AfxOleLockApp](../mfc/reference/application-control.md#afxolelockapp) a [funkci AfxOleUnlockApp](../mfc/reference/application-control.md#afxoleunlockapp) aktualizují počet aktivních objektů aplikace. Pokud je tento počet nenulový, aplikace se neukončí, když uživatel zvolí možnost Zavřít ze systémové nabídky nebo ukončit v nabídce soubor. Místo toho je hlavní okno aplikace skryté (ale nebude zničeno), dokud nebudou dokončeny všechny požadavky klientů na zpracování. `AfxOleLockApp` Obvykle a `AfxOleUnlockApp` jsou volány v konstruktorech a destruktorech, v uvedeném pořadí, třídy, které podporují automatizaci.

V některých případech vynutí ukončení serveru, zatímco klient stále obsahuje odkaz na objekt. Například prostředek, na kterém závisí Server, může být nedostupný, což způsobí, že server narazí na chybu. Uživatel může také zavřít dokument serveru, který obsahuje objekty, na které mají odkazy jiné aplikace.

V Windows SDK naleznete v tématech `IUnknown::AddRef` a `IUnknown::Release`.

## <a name="see-also"></a>Viz také:

[Automatizační servery](../mfc/automation-servers.md)<br/>
[AfxOleCanExitApp](../mfc/reference/application-control.md#afxolecanexitapp)
