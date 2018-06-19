---
title: 'OLE – pozadí: Implementace MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IMarshall
- IMoniker
dev_langs:
- C++
helpviewer_keywords:
- MFC libraries, implementing
- OLE MFC library implementation
- OLE IMarshal interface
- IMoniker interface, MFC
- IMarshall class [MFC]
- OLE, compound files
- OLE IMoniker interface
- OLE IUnknown
ms.assetid: 2b67016a-d78e-4d60-925f-c28ec8fb6180
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 124bec9bfdbdc4e39bab71a80f77d7a06d8444a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349996"
---
# <a name="ole-background-mfc-implementation"></a>OLE – pozadí: Implementace MFC
Kvůli velikost a složitost nezpracovaná OLE rozhraní API volání se přímo k psaní aplikací OLE může být časově velmi náročná. Cílem společnosti Microsoft Foundation Class Library implementace OLE je snížit objem práce, kterou je nutné provést pro psaní aplikací plně funkční, podporující OLE.  
  
 Tento článek vysvětluje části OLE API, které nejsou implementované uvnitř MFC. Diskuse také vysvětluje, jak mapuje co je implementována do části OLE sady Windows SDK.  
  
##  <a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a> Části OLE není implementováno knihovna tříd  
 V prostředí MFC nejsou přímo zadat několik rozhraní a funkcí OLE. Pokud chcete tyto funkce používají, můžete rozhraní OLE API volat přímo.  
  
 Imoniker – rozhraní  
 `IMoniker` Rozhraní je implementováno modulem knihovny tříd (například `COleServerItem` třída), ale nebyla dříve vystavena programátorů. Další informace o tomto rozhraní najdete v části implementace technologie OLE Přezdívka v části OLE sady Windows SDK. Viz však také třída [CMonikerFile](../mfc/reference/cmonikerfile-class.md) a [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).  
  
 IUnknown a imarshal – rozhraní  
 **IUnknown** rozhraní je implementováno modulem knihovny tříd, ale není vystavený programátorů. **Imarshal –** rozhraní není implementována knihovna tříd, ale se používá interně. Automatizační servery vyvíjené v knihovně tříd již mít zařazování možnosti, které jsou součástí.  
  
 DOCFILES (složené soubory)  
 Složené soubory jsou částečně podporovány knihovny tříd. Žádná z funkcí, které přímo manipulovat s složené soubory nad rámec vytvoření jsou podporovány. MFC používá třídu **COleFileStream** pro podporu zpracování datových proudů s funkce standardní souboru. Další informace najdete v článku [kontejnery: složené soubory](../mfc/containers-compound-files.md).  
  
 Servery v rámci procesu a objekt obslužné rutiny  
 Servery v rámci procesu a obslužné rutiny objektu povolit implementace visual úpravy dat nebo úplné objekty modelu COM (Component Object) v dynamické knihovně (DLL). K tomuto účelu můžete implementovat vaše knihovna DLL pomocí volání OLE API přímo. Ale pokud píšete serveru automatizace a váš server nemá žádné uživatelské rozhraní, můžete použít objekty AppWizard a nastavit váš server v rámci procesu kompletně umístit do knihovny DLL. Další informace o těchto tématech najdete v tématu [automatizační servery](../mfc/automation-servers.md).  
  
> [!TIP]
>  Nejjednodušší způsob, jak implementovat serveru automatizace je pro jeho umístění v knihovně DLL. MFC podporuje tuto metodu.  
  
 Další informace o tom, jak třídy Microsoft Foundation OLE implementovat rozhraní OLE najdete v tématu MFC – technické poznámky [38](../mfc/tn038-mfc-ole-iunknown-implementation.md), [39](../mfc/tn039-mfc-ole-automation-implementation.md), a [40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).  
  
## <a name="see-also"></a>Viz také  
 [OLE – pozadí](../mfc/ole-background.md)   
 [OLE – pozadí: Strategie implementace](../mfc/ole-background-implementation-strategies.md)

