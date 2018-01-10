---
title: "Dělení na vlákna modely a kritické oddíly třídy (ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.atl.threads.models
dev_langs: C++
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1501fe4f761b9bc8775018d6566ceff5fb0aa477
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="threading-models-and-critical-sections-classes"></a>Dělení na vlákna modely a kritické oddíly třídy
Následující třídy definují dělení na vlákna modelu a kritická sekce:  
  
-   [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md) implementuje server COM ve fondu vláken, apartment model.  
  
-   [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md) poskytuje metody pro implementaci serveru COM ve fondu vláken, apartment model.  
  
-   [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md) poskytuje metody vláken pro zvyšování a dekrementace proměnné. Poskytuje kritická sekce.  
  
-   [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md) poskytuje metody vláken pro zvyšování a dekrementace proměnné. Neposkytuje kritická sekce.  
  
-   [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md) poskytuje metody pro zvyšování a dekrementace proměnné. Neposkytuje kritická sekce.  
  
-   [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel) určuje příslušné třídy modelu vláken pro třídu jednoho objektu.  
  
-   [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel) určuje příslušnou třídu modelu vláken pro objekt, který je globálně dostupnou.  
  
-   [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md) obsahuje metody pro získání a uvolněním kritická sekce. Kritická sekce je automaticky inicializován.  
  
-   [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md) obsahuje metody pro získání a uvolněním kritická sekce. Kritická sekce musí být explicitně inicializován.  
  
-   [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md) zrcadlí metody v `CComCriticalSection` bez zadání kritická sekce. Metody v `CComFakeCriticalSection` nic nestane.  
  
-   [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) poskytuje funkce vytváření CRT vlákna. Tuto třídu používejte, pokud vlákno používat funkce CRT.  
  
-   [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md) poskytuje funkce vytváření vlákna systému Windows. Tuto třídu používejte, pokud vlákno nebude používat funkce CRT.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../atl/atl-class-overview.md)

