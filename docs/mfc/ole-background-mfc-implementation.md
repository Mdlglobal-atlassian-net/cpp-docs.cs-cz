---
title: 'OLE – pozadí: Implementace MFC'
ms.date: 11/04/2016
f1_keywords:
- IMarshall
- IMoniker
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
ms.openlocfilehash: 25c98c3683a8656bb5188f22d0464d25a4901f49
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364535"
---
# <a name="ole-background-mfc-implementation"></a>OLE – pozadí: Implementace MFC

Vzhledem k velikosti a složitosti nezpracované rozhraní OLE API volání přímo k zápisu aplikace OLE může být velmi časově náročné. Cílem implementace ole knihovny tříd microsoft foundation je snížit množství práce, kterou je třeba provést při psaní plně vybavených aplikací podporujících ole.

Tento článek vysvětluje části rozhraní OLE API, které nebyly implementovány uvnitř knihovny MFC. Diskuse také vysvětluje, jak se implementuje, co se mapuje do části OLE sady Windows SDK.

## <a name="portions-of-ole-not-implemented-by-the-class-library"></a><a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a>Části OLE, které nejsou implementovány knihovnou tříd

Několik rozhraní a funkce OLE nejsou přímo k dispozici knihovnou MFC. Pokud chcete použít tyto funkce, můžete volat rozhraní OLE API přímo.

IMoniker Interface `IMoniker` Rozhraní je implementováno knihovnou `COleServerItem` tříd (například třídou), ale nebylo dříve vystaveno programátorovi. Další informace o tomto rozhraní naleznete v tématu OLE Moniker Implementations v části OLE sady Windows SDK. Viz však také třída [CMonikerFile](../mfc/reference/cmonikerfile-class.md) a [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).

Rozhraní IUnknown a IMarshal Rozhraní `IUnknown` je implementováno knihovnou tříd, ale není vystaveno programátorovi. Rozhraní `IMarshal` není implementováno knihovnou tříd, ale používá se interně. Automatizační servery vytvořené pomocí knihovny tříd již mají vestavěné možnosti zařazování.

Docfiles (Složené soubory) Složené soubory jsou částečně podporovány knihovnou tříd. Žádná z funkcí, které přímo manipulovat složené soubory mimo vytvoření jsou podporovány. Knihovna MFC používá třídu `COleFileStream` k podpoře manipulace s datovými proudy se standardními funkcemi souborů. Další informace naleznete v článku [Kontejnery: Složené soubory](../mfc/containers-compound-files.md).

Inprocess servery a obslužné rutiny objektů V procesu a obslužné rutiny objektů umožňují implementaci vizuálních editačních dat nebo úplných objektů COM (Component Object Model) v dynamicko-linkové knihovně (DLL). Chcete-li to provést, můžete implementovat knihovnu DLL voláním rozhraní OLE API přímo. Pokud však píšete automatizační server a server nemá žádné uživatelské rozhraní, můžete pomocí Průvodce aplikací vytvořit server v procesu a zcela jej vložit do knihovny DLL. Další informace o těchto tématech naleznete v [tématu Automation Servers](../mfc/automation-servers.md).

> [!TIP]
> Nejjednodušší způsob, jak implementovat server automatizace je umístit do DLL. Knihovna MFC podporuje tento přístup.

Další informace o tom, jak třídy OLE aplikace OLE aplikace Microsoft Foundation implementují rozhraní OLE, naleznete v technických poznámkách knihovny MFC [38](../mfc/tn038-mfc-ole-iunknown-implementation.md), [39](../mfc/tn039-mfc-ole-automation-implementation.md)a [40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="see-also"></a>Viz také

[OLE – pozadí](../mfc/ole-background.md)<br/>
[OLE – pozadí: Strategie implementace](../mfc/ole-background-implementation-strategies.md)
