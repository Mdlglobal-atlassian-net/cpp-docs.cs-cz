---
title: 'OLE – pozadí: Implementace v prostředí MFC'
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
ms.openlocfilehash: f793c7d7303a49057e46c32eb658ea7eea8e9ccc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186726"
---
# <a name="ole-background-mfc-implementation"></a>OLE – pozadí: Implementace v prostředí MFC

Kvůli velikosti a složitosti nezpracovaná OLE rozhraní API ho přímo pro psaní aplikací OLE volání může být časově velmi náročné. Cílem implementace knihovny Microsoft Foundation Class OLE je snížit množství práce, kterou musíte udělat pro psaní aplikací plně funkční, podporující OLE.

Tento článek vysvětluje části OLE API, které nejsou implementované uvnitř knihovny MFC. Diskuse také vysvětluje, jak je implementován co mapuje na OLE část sady Windows SDK.

##  <a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a> Části OLE není implementované knihovny tříd

Několik rozhraní a funkce OLE se neposkytují přímo v prostředí MFC. Pokud chcete používat tyto funkce, je možné volat rozhraní OLE API přímo.

Imoniker – rozhraní `IMoniker` rozhraní je implementováno knihovnou tříd (například `COleServerItem` třídy), ale nebyla dříve byl zpřístupněn na programátorovi. Další informace o tomto rozhraní naleznete v tématu implementace technologie OLE Moniker OLE část sady Windows SDK. Nicméně viz také třída [cmonikerfile –](../mfc/reference/cmonikerfile-class.md) a [casyncmonikerfile –](../mfc/reference/casyncmonikerfile-class.md).

IUnknown a rozhraní imarshal – `IUnknown` rozhraní je implementované knihovny tříd, ale není dostupné na programátorovi. `IMarshal` Rozhraní není implementováno pomocí knihovny tříd, ale používá se interně. Automatizační servery sestavený pomocí knihovny třídy již mít zařazování možností integrovaných.

Knihovna tříd podporuje částečně složené soubory DOCFILES (složených souborů). Žádnou z funkcí, které přímo pracovat nad rámec vytváření složených souborů nejsou podporovány. Knihovna MFC používá třídy `COleFileStream` pro podporu zpracování datových proudů s využitím functions standardní soubor. Další informace najdete v článku [kontejnerů: Složené soubory](../mfc/containers-compound-files.md).

Vnitroprocesové servery a obslužné rutiny objekt vnitroprocesové servery a objekt obslužné rutiny umožňují provádění vizuální úpravy dat nebo úplné objekty modelu COM (Component Object) v dynamická knihovna (DLL). K tomu je možné implementovat vaše knihovna DLL prostřednictvím přímého volání OLE API. Nicméně pokud píšete automatizační server a server nemá žádné uživatelské rozhraní, můžete použít AppWizard kompletně umístit do knihovny DLL a aby byl váš server v procesový server. Další informace o těchto tématech najdete v tématu [automatizační servery](../mfc/automation-servers.md).

> [!TIP]
>  Nejjednodušší způsob, jak implementovat automatizačního serveru je umístit v knihovně DLL. MFC podporuje tento přístup.

Další informace o způsobu implementace tříd Microsoft Foundation OLE rozhraní OLE, najdete v článku MFC – technické poznámky [38](../mfc/tn038-mfc-ole-iunknown-implementation.md), [39](../mfc/tn039-mfc-ole-automation-implementation.md), a [40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="see-also"></a>Viz také:

[OLE – pozadí](../mfc/ole-background.md)<br/>
[OLE – pozadí: Strategie implementace](../mfc/ole-background-implementation-strategies.md)
