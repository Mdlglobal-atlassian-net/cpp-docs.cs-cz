---
title: "Body připojení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d8bbb131aa5d4ce1b12cba84c3928b80a8b2a7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="connection-points"></a>Body připojení
Tento článek vysvětluje, jak implementovat spojovací body (dříve označované jako OLE spojovací body) pomocí třídy MFC `CCmdTarget` a `CConnectionPoint`.  
  
 V minulosti definované modelu COM (Component Object) obecné mechanismus (**IUnknown::QueryInterface**), povolené objekty k implementaci a zpřístupnění funkce v rozhraní. Však nebyl definován odpovídající mechanismus, který povolené objekty, které chcete zpřístupnit jejich schopnost volání konkrétní rozhraní. To znamená, COM definovaný jak příchozí ukazatelé na objekty byly zpracovány (ukazatele na tento objekt rozhraní), ale nemá model explicitní pro odchozí rozhraní (ukazatele obsahuje objekt do jiné objekty rozhraní). COM teď má model, volá se spojovací body podporující tuto funkci.  
  
 Připojení se skládá ze dvou částí: objekt volání rozhraní, jako zdroj a objekt implementující rozhraní nazývá jímky. Bod připojení je rozhraní vystavené zdroji. Díky zpřístupnění spojovací bod, umožňuje zdroj jímky ke zřízení spojení sama na sebe (zdroj). Prostřednictvím připojení bodu mechanismus ( **IConnectionPoint –** rozhraní), je předán ukazatel rozhraní podřízený ke zdrojovému objektu. Ukazatel this poskytuje zdroji s přístupem k implementaci podřízený sadu členské funkce. Aktivovat událost implementované jímky, můžete v zdroji voláním vhodný způsob provádění jímky. Následující obrázek ukazuje připojení bodu právě popsané.  
  
 ![Implementována spojovací bod](../mfc/media/vc37lh1.gif "vc37lh1")  
Implementovaný bod připojení  
  
 Tento model v implementuje MFC [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md) a [CCmdTarget](../mfc/reference/ccmdtarget-class.md) třídy. Třídy odvozené od **CConnectionPoint** implementovat **IConnectionPoint –** rozhraní, které se používá ke zveřejnění body připojení k jiným objektům. Třídy odvozené od `CCmdTarget` implementovat **IConnectionPointContainer** rozhraní, které můžete vytvořit výčet všech bodů dostupné připojení objektu nebo najít konkrétní spojovacího bodu.  
  
 Pro každý bod připojení implementována ve třídě je potřeba deklarovat součást připojení, který implementuje spojovací bod. Pokud budete implementovat jednu nebo více bodů připojení, je také potřeba deklarovat mapu jednoho připojení v třídě. Mapy připojení je tabulka nepodporuje ovládací prvek ActiveX bodů připojení.  
  
 Následující příklady ukazují mapy jednoduché připojení a jedno připojení k bodu. V prvním příkladu deklaruje mapy připojení a čárky. v druhém příkladu implementuje mapy a bod. Všimněte si, že `CMyClass` musí být `CCmdTarget`-odvozené třídy. V prvním příkladu kódu je vložen v deklaraci třídy, v části **chráněné** části:  
  
 [!code-cpp[NVC_MFCConnectionPoints#1](../mfc/codesnippet/cpp/connection-points_1.h)]  
  
 `BEGIN_CONNECTION_PART` a **end_connection_part –** makra deklarovat třídu embedded `XSampleConnPt` (odvozený od `CConnectionPoint`), aby implementuje tuto konkrétní spojovacího bodu. Pokud chcete přepsat všechny `CConnectionPoint` členské funkce nebo přidání členské funkce vlastní, deklarovat je mezi těmito dvěma makra. Například `CONNECTION_IID` makro přepsání `CConnectionPoint::GetIID` – členská funkce, když je umístěná mezi těmito dvěma makra.  
  
 V druhém příkladu kódu se vloží do ovládacího prvku implementace soubor (sada). Tento kód implementuje mapy připojení, která obsahuje bod připojení, `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../mfc/codesnippet/cpp/connection-points_2.cpp)]  
  
 Pokud vaše třída má více než jedno připojení k bodu, vložte další `CONNECTION_PART` makra mezi `BEGIN_CONNECTION_MAP` a `END_CONNECTION_MAP` makra.  
  
 Nakonec přidejte volání `EnableConnections` v konstruktoru třídy. Příklad:  
  
 [!code-cpp[NVC_MFCConnectionPoints#3](../mfc/codesnippet/cpp/connection-points_3.cpp)]  
  
 Jakmile se tento kód byl vložen, vaše `CCmdTarget`-odvozené třídě poskytuje bod připojení pro **ISampleSink** rozhraní. Následující obrázek ukazuje tento příklad.  
  
 ![Spojovací bod je implementována pomocí knihovny MFC](../mfc/media/vc37lh2.gif "vc37lh2")  
Bod připojení implementováno s MFC  
  
 Obvykle spojovací body podporu "vícesměrového vysílání" – možnost všesměrové vysílání pro více jímky připojené k stejné rozhraní. Následující fragment příklad ukazuje, jak vícesměrového vysílání pomocí iterace každý podřízený ve spojovacím bodě:  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../mfc/codesnippet/cpp/connection-points_4.cpp)]  
  
 Tento příklad načte aktuální sadu připojení na `SampleConnPt` spojovací bod pomocí volání `CConnectionPoint::GetConnections`. Ji pak iteruje v rámci připojení a volání **ISampleSink::SinkFunc** na všechny aktivní připojení.  
  
## <a name="see-also"></a>Viz také  
 [MFC COM](../mfc/mfc-com.md)

