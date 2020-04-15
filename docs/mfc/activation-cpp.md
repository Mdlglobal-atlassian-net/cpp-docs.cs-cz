---
title: Aktivace (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], activation
- OLE items [MFC], visual editing
- activation [MFC]
- OLE [MFC], in-place activation
- OLE [MFC], activation
- in-place activation, embedded and linked items
- activating objects
- visual editing, activation
- visual editing
- documents [MFC], OLE
- embedded objects [MFC]
- OLE [MFC], editing
- in-place activation
- activation [MFC], embedded OLE items
- OLE activation [MFC]
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
ms.openlocfilehash: 9f3fba71002a19a0be0e3429a0faeeefb7c65197
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354171"
---
# <a name="activation-c"></a>Aktivace (C++)

Tento článek vysvětluje roli aktivace ve vizuální úpravy položek OLE. Poté, co uživatel vložil položku OLE do dokumentu kontejneru, může být nutné ji použít. Chcete-li to provést, uživatel poklepe na položku, která tuto položku aktivuje. Nejčastější aktivitou aktivace jsou úpravy. Mnoho aktuálních položek OLE při aktivaci pro úpravy způsobí, že nabídky a panely nástrojů v aktuálním okně rámce se změní tak, aby odrážely ty, které patří do serverové aplikace, která položku vytvořila. Toto chování, známé jako aktivace na místě, umožňuje uživateli upravit libovolnou vloženou položku ve složeném dokumentu, aniž by opustil okno dokumentu kontejneru.

Je také možné upravit vložené položky OLE v samostatném okně. K tomu dojde, pokud kontejner nebo serverová aplikace nepodporuje aktivaci na místě. V tomto případě, když uživatel poklepe na vloženou položku, serverová aplikace se spustí v samostatném okně a vložená položka se zobrazí jako vlastní dokument. Uživatel uúpravy položky v tomto okně. Po dokončení úprav uživatel zavře serverovou aplikaci a vrátí se do aplikace kontejneru.

Jako alternativu může uživatel zvolit "otevřít úpravy" pomocí ** \<příkazu objektu> Otevřít** v nabídce **Úpravy.** Tím se objekt otevře v samostatném okně.

> [!NOTE]
> Úpravy vložených položek v samostatném okně bylo standardní chování ve verzi 1 OLE a některé aplikace OLE může podporovat pouze tento styl úprav.

Aktivace na místě podporuje přístup k vytváření dokumentů zaměřený na dokumenty. Uživatel může považovat složený dokument za jednu entitu a pracovat na něm bez přepínání mezi aplikacemi. Aktivace na místě se však používá pouze pro vložené položky, nikoli pro propojené položky: musí být upraveny v samostatném okně. Důvodem je, že propojená položka je ve skutečnosti uložena na jiném místě. Úpravy propojené položky probíhá v rámci skutečného kontextu dat, tj. Úprava propojené položky v samostatném okně připomene uživateli, že data patří do jiného dokumentu.

Knihovna MFC nepodporuje vnořenou aktivaci na místě. Pokud vytvoříte aplikaci kontejneru nebo serveru a tento kontejner/server je vložen do jiného kontejneru a aktivován na místě, nemůže na místě aktivovat objekty vložené uvnitř něj.

Co se stane s vloženou položkou, když uživatel poklepe na ji závisí na slovesa definovaná pro položku. Další informace naleznete [v tématu Aktivace: Slovesa](../mfc/activation-verbs.md).

## <a name="see-also"></a>Viz také

[OLE](../mfc/ole-in-mfc.md)<br/>
[Containers](../mfc/containers.md)<br/>
[Servery](../mfc/servers.md)
