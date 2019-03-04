---
title: 'Automatizační servery: Problémy životnosti objektů'
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
ms.openlocfilehash: f9dbc6e4f321ba10fdffa013c158d53b84331e30
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293573"
---
# <a name="automation-servers-object-lifetime-issues"></a>Automatizační servery: Problémy životnosti objektů

Pokud klienta automatizace vytvoří nebo položky OLE se aktivuje, odešle server klienta ukazatel na tento objekt. Klient vytvoří odkaz na objekt pomocí volání funkce OLE [IUnknown::AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref). Tento odkaz je v platnosti až do volání klienta [IUnknown::Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release). (Klientských aplikací napsaných pomocí knihovny serveru Microsoft Foundation Class OLE – třídy nemusí provádět tyto volání; provádí se rozhraní framework.) Odkazy na objekt může zřídit systém technologie OLE a samotný server. Server by neměla zničit objekt tak dlouho, dokud externí odkazy na objekt zůstávají v platnosti.

Rozhraní framework udržuje interní počet počet odkazů na libovolný server objekt odvozený od [CCmdTarget –](../mfc/reference/ccmdtarget-class.md). Tento počet aktualizuje, když klient služby Automation nebo jiná entita přidá nebo uvolní odkaz na objekt.

Jakmile je počet odkazů 0, volá framework virtuální funkce [CCmdTarget::OnFinalRelease](../mfc/reference/ccmdtarget-class.md#onfinalrelease). Výchozí implementace této funkce se volá **odstranit** operátor tento objekt odstranit.

Knihovny Microsoft Foundation Class poskytuje další funkce pro řízení chování aplikace při externí klienti mají odkazy na objekty aplikaci. Kromě zachování počet odkazů na každý objekt, servery udržují globální počet aktivních objektů. Globální funkce [AfxOleLockApp](../mfc/reference/application-control.md#afxolelockapp) a [funkci AfxOleUnlockApp](../mfc/reference/application-control.md#afxoleunlockapp) aktualizovat aplikace počet aktivních objektů. Pokud je tento počet nenulovou hodnotu, aplikace se neukončí, když se uživatel rozhodne zavření ze systémové nabídky nebo ukončit v nabídce Soubor. Místo toho hlavního okna aplikace je skrytý (to však nejsou zničeny) až do všechny čekající klienta, které požadavky byly dokončeny. Obvykle `AfxOleLockApp` a `AfxOleUnlockApp` jsou volány v konstruktory a destruktory, resp. třídy, které podporují služby Automation.

Někdy okolností vynutit server ukončit, když je klient stále obsahuje odkaz na objekt. Například prostředků, na které závisí na serveru se můžou stát nedostupnými, způsobí serveru dojde k chybě. Uživatel může také zavřít dokument serveru, který obsahuje objekty, na které odkazují jiné aplikace.

V sadě Windows SDK, naleznete v tématu `IUnknown::AddRef` a `IUnknown::Release`.

## <a name="see-also"></a>Viz také:

[Automatizační servery](../mfc/automation-servers.md)<br/>
[AfxOleCanExitApp](../mfc/reference/application-control.md#afxolecanexitapp)
