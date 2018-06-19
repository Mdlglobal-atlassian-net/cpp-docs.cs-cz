---
title: 'Automatizační servery: Problematika životnosti objektů | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e27812c20a64f5472c29a66298bcdec30bf4ef2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341797"
---
# <a name="automation-servers-object-lifetime-issues"></a>Automatizační servery: Problematika životnosti objektů
Pokud klienta automatizace vytvoří nebo aktivuje OLE položku, odešle server klienta ukazatel na tento objekt. Klient pro zakládá odkaz na objekt prostřednictvím volání funkce OLE [IUnknown::AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379). Tento odkaz je v platnosti do volání klienta [IUnknown::Release](http://msdn.microsoft.com/library/windows/desktop/ms682317). (Klientské aplikace napsané pomocí knihovny serveru Microsoft Foundation Class OLE – třídy nemusí provádět tyto volání; rozhraní nemá tak.) Systém OLE a samotný server může vytvořit odkazy na objekt. Server by neměla nezničí objekt tak dlouho, dokud externí odkazy do objektu zůstávají v platnosti.  
  
 Rozhraní framework udržuje interní počet počet odkazů na libovolný server objekt odvozené od [CCmdTarget](../mfc/reference/ccmdtarget-class.md). Tento počet je aktualizována při klientem automatizace nebo jiné entity přidá nebo odkaz na objekt uvolní.  
  
 Pokud počet odkazů se změní na 0, volá framework virtuální funkce [CCmdTarget::OnFinalRelease](../mfc/reference/ccmdtarget-class.md#onfinalrelease). Výchozí implementace této funkce volá **odstranit** operátor tento objekt odstranit.  
  
 Knihovny Microsoft Foundation Class zajišťuje další funkce pro řízení chování aplikace při externí klienti mají odkazy na objekty aplikace. Kromě toho, údržbu a počet odkazů na každý objekt, Udržovat servery globální počet aktivních objektů. Globální funkce [afxolelockapp –](../mfc/reference/application-control.md#afxolelockapp) a [afxoleunlockapp –](../mfc/reference/application-control.md#afxoleunlockapp) aktualizace aplikace počet aktivních objektů. Pokud je to počet nenulové hodnoty, aplikace se nezavře, když uživatel vybere zavřít z nabídky systému nebo ukončení v nabídce Soubor. Místo toho hlavní okno aplikace je skrytý (ale není ztraceny) až všechny čekající na vyřízení klienta, které se dokončily požadavky. Obvykle `AfxOleLockApp` a `AfxOleUnlockApp` se nazývají v konstruktorech a destruktory, v uvedeném pořadí, tříd, které podporují automatizace.  
  
 Někdy okolností vynutit serveru ukončit, zatímco je klient stále obsahuje odkaz na objekt. Například může stát prostředků, na které závisí serveru není k dispozici, způsobuje serveru dojde k chybě. Uživatel může také zavřít serveru dokumentu, který obsahuje objekty, na které jiné aplikace mají odkazy.  
  
 Ve Windows SDK najdete v části `IUnknown::AddRef` a `IUnknown::Release`.  
  
## <a name="see-also"></a>Viz také  
 [Automatizační servery](../mfc/automation-servers.md)   
 [Afxolecanexitapp –](../mfc/reference/application-control.md#afxolecanexitapp)

