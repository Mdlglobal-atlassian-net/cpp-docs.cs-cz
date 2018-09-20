---
title: Body připojení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IConnectionPoint
dev_langs:
- C++
helpviewer_keywords:
- IConnectionPoint interface
- connections, connection points
- OLE COM connection points
- MFC COM, connection points
- COM, connection points
- interfaces, IConnectionPoint
- MFC, COM support
- connection points [MFC]
- CCmdTarget class [MFC], and connection points
- sinks, connection points
ms.assetid: bc9fd7c7-8df6-4752-ac8c-0b177442c88d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0df8ed5dd3cb918c8735f5249a08d3e0d83af61
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438547"
---
# <a name="connection-points"></a>Body připojení

Tento článek vysvětluje, jak implementovat spojovací body (dříve OLE spojovací body) pomocí tříd knihovny MFC `CCmdTarget` a `CConnectionPoint`.

V minulosti, definované modelu COM (Component Object) obecný mechanismus (`IUnknown::QueryInterface`*), která může objekty k implementaci a zpřístupnění funkcí v rozhraní. Však nebyl definován odpovídající mechanismus, který povolené objekty k vystavení jejich schopnost volání konkrétní rozhraní. To znamená, definované jak příchozí ukazatele na objekty modelu COM byly zpracovány (odkazy na tento objekt rozhraní), ale neměl explicitní model pro odchozí rozhraní (ukazatele na objekt obsahuje další objekty rozhraní). COM nyní používá model, volá se spojovací body podporující tuto funkci.

Připojení má dvě části: objekt volání rozhraní jako zdroj a objekt implementující rozhraní, nazývá jímky. Spojovací bod je rozhraní vystavené ve zdroji. Zveřejněním spojovací bod umožňuje zdroji jímky k navázání připojení k samotné (zdroj). Prostřednictvím připojení příkaz mechanismus ( `IConnectionPoint` rozhraní), je předán ukazatel na rozhraní stoku se zdrojovým objektem. This – ukazatel poskytuje zdroj s přístupem k implementaci jímky sadu členské funkce. Chcete-li vyvolat událost implementované jímka zdroji můžete volat, odpovídající metodu jímky implementace. Následující obrázek ukazuje připojení bodu právě popsanou.

![Implementovat bod připojení](../mfc/media/vc37lh1.gif "vc37lh1") implementovat přípojný bod

Knihovna MFC implementuje tento model [cconnectionpoint –](../mfc/reference/cconnectionpoint-class.md) a [CCmdTarget –](../mfc/reference/ccmdtarget-class.md) třídy. Třídy odvozené z `CConnectionPoint` implementovat `IConnectionPoint` rozhraní, používá k vystavení spojovací body na jiné objekty. Třídy odvozené z `CCmdTarget` implementovat `IConnectionPointContainer` rozhraní, které můžete vytvořit výčet všech body k dispozici připojení objektu nebo vyhledejte konkrétní spojovací bod.

Pro každý bod připojení implementována ve třídě je třeba deklarovat část připojení, která implementuje bod připojení. Pokud se rozhodnete implementovat jeden nebo více bodů připojení, musíte také deklarovat mapu jedno připojení ve své třídě. Mapy připojení je tabulka spojovacích bodů podporována ovládacím prvkem ActiveX.

Následující příklady ukazují jednoduchý připojení mapy a jeden přípojný bod. První příklad deklaruje mapu připojení a čárky v druhém příkladu implementuje mapy a bodu. Všimněte si, že `CMyClass` musí být `CCmdTarget`-odvozené třídy. V prvním příkladu kódu je vložen v deklaraci třídy, v části **chráněné** části:

[!code-cpp[NVC_MFCConnectionPoints#1](../mfc/codesnippet/cpp/connection-points_1.h)]

**BEGIN_CONNECTION_PART** a **END_CONNECTION_PART** makra deklarovat třídu vložený `XSampleConnPt` (odvozený od `CConnectionPoint`), že implementuje toto konkrétní přípojný bod. Pokud je zapotřebí přepsat některé `CConnectionPoint` členské funkce nebo přidat vlastní členské funkce, je deklarovat mezi těmito dvěma makra. Například `CONNECTION_IID` – makro přepsání `CConnectionPoint::GetIID` členské funkce při umístěny mezi těmito dvěma makra.

V druhém příkladu kódu je vložen do ovládacího prvku implementace souboru (.cpp). Tento kód implementuje mapy připojení, která obsahuje bod připojení, `SampleConnPt`:

[!code-cpp[NVC_MFCConnectionPoints#2](../mfc/codesnippet/cpp/connection-points_2.cpp)]

Pokud vaše třída má více než jedno připojení bodu, vložit další **CONNECTION_PART** makra mezi **BEGIN_CONNECTION_MAP** a **END_CONNECTION_MAP** makra.

Nakonec přidejte volání do `EnableConnections` v konstruktoru třídy. Příklad:

[!code-cpp[NVC_MFCConnectionPoints#3](../mfc/codesnippet/cpp/connection-points_3.cpp)]

Jakmile tento kód byl vložen, vaše `CCmdTarget`-odvozené třídě poskytuje bod připojení pro `ISampleSink` rozhraní. Následující obrázek ukazuje tento příklad.

![Spojovací bod implementovaná pomocí knihovny MFC](../mfc/media/vc37lh2.gif "vc37lh2") A připojení bodu implementovaná pomocí knihovny MFC

Obvykle spojovací body podporují "vícesměrové vysílání" – možnost vysílání více jímky připojené ke stejnému rozhraní. Následující příklad fragmentu ukazuje, jak vícesměrového vysílání podle iterace v rámci každé jímky najdete v bodě připojení:

[!code-cpp[NVC_MFCConnectionPoints#4](../mfc/codesnippet/cpp/connection-points_4.cpp)]

Tento příklad načte aktuální sadu připojení na `SampleConnPt` spojovací bod voláním `CConnectionPoint::GetConnections`. Pak Iteruje přes připojení a volání `ISampleSink::SinkFunc` na každé aktivní připojení.

## <a name="see-also"></a>Viz také

[MFC COM](../mfc/mfc-com.md)

