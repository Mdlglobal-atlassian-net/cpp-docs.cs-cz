---
title: 'OLE – pozadí: Kontejnery a servery'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE full-server applications [MFC]
- server applications [MFC], communication with containers
- full-server [MFC]
- server applications [MFC], requirements
- server applications [MFC], defined
- OLE server applications [MFC], about server applications
- server applications [MFC], full-server vs. mini-server
- OLE server applications [MFC], mini-server applications
- OLE containers [MFC], container applications
- containers [MFC], OLE container applications
- server applications [MFC]
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
ms.openlocfilehash: 3c696f1e99a73cbce6f1ff749de937297b28d88b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616922"
---
# <a name="ole-background-containers-and-servers"></a>OLE – pozadí: Kontejnery a servery

Aplikace typu kontejner je aplikace, která můžete začlenit do vlastní dokumenty vložené nebo propojené položky. Dokumenty, které spravuje aplikace typu kontejner musí být schopen ukládat a zobrazovat součásti dokumentu OLE, jakož i data vytvořená systémem samotná aplikace. Aplikace typu kontejner musí také umožňují uživatelům vkládání nových položek nebo upravit existující položky aktivací serverové aplikace, pokud je to nezbytné. V článku jsou uvedené požadavky na uživatelské rozhraní aplikace typu kontejner [kontejnery: problémy uživatelského rozhraní](../mfc/containers-user-interface-issues.md).

Serverová aplikace nebo součásti aplikace je aplikace, můžete vytvořit komponenty dokumentu OLE pro použití aplikací typu kontejner. Server aplikace obvykle podporují přetahování nebo tak, aby aplikace typu kontejner můžete vložit data jako vložené nebo propojené položky kopírování svá data do schránky. Aplikace může být kontejner a serverem.

Většina serverů jsou samostatné aplikace nebo úplná serverů. jejich lze spustit buď jako samostatné aplikace nebo může být spuštěn aplikace typu kontejner. Miniserver je zvláštní druh serverovou aplikaci, která může být spuštěn pouze kontejner. Není možné spustit jako samostatnou aplikaci. Příklady miniservers jsou servery Microsoft Draw a Microsoft Graph.

Kontejnery a servery nekomunikují přímo. Místo toho komunikují prostřednictvím OLE systému dynamické knihovny (DLL). Tyto knihovny DLL poskytují funkce, které volají kontejnery a servery a kontejnery a servery poskytují funkce zpětného volání, které volají knihovny DLL.

Pomocí to znamená, že komunikace, kontejner není potřeba znát podrobnosti implementace serverová aplikace. To umožňuje kontejneru tak, aby přijímal položky vytvořené libovolný server, aniž byste museli definovat typy serverů, se kterými můžete pracovat. Uživatel aplikace typu kontejner v důsledku toho můžete využít výhod budoucí aplikace a datových formátů. Pokud tyto nové aplikace jsou komponenty OLE, pak bude mít k začlenění položek vytvořený těmito aplikacemi složeného dokumentu.

## <a name="see-also"></a>Viz také

[OLE – pozadí](../mfc/ole-background.md)<br/>
[OLE – pozadí: Implementace MFC](../mfc/ole-background-mfc-implementation.md)<br/>
[Kontejnery](../mfc/containers.md)<br/>
[Servery](../mfc/servers.md)<br/>
[Kontejnery: Klientské položky](../mfc/containers-client-items.md)<br/>
[Servery: Serverové položky](../mfc/servers-server-items.md)

