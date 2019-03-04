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
ms.openlocfilehash: a6009e5209ce71c6eed28faff2f55792a64de408
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276946"
---
# <a name="activation-c"></a>Aktivace (C++)

Tento článek vysvětluje roli aktivovat vizuální úpravy položky OLE. Poté, co uživatel má vložené položky OLE v dokumentu kontejneru, bude pravděpodobně nutné použít. K tomuto účelu uživatel dvakrát klikne na položku, která se aktivuje danou položku. Nejčastěji se vyskytujících aktivity pro aktivaci upravuje. Mnoho aktuální položky OLE, když se aktivuje pro úpravy, způsobit nabídek a panelů nástrojů v aktuální okno rámce, chcete-li změnit tak, aby odrážely těch, které patří do serverové aplikace, která vytvořila tuto položku. Toto chování, známé jako aktivace na místě, umožňuje uživateli upravovat libovolnou položku vložený ve složeném dokumentu bez opuštění okna dokumentu kontejneru.

Je také možné upravit vložené položky OLE v samostatném okně. To se stane, pokud aplikace kontejneru nebo server nepodporuje aktivace na místě. V takovém případě při poklepání vložená položka. serverová aplikace spuštěna v samostatném okně a vložená položka je zobrazena jako svůj vlastní dokument. Uživatel upravuje položky v tomto okně. Po dokončení úprav uživatel serverové aplikace se zavře a vrátí do aplikace typu kontejner.

Jako alternativu, uživatel může zvolit "Otevřít úpravy" s  **\<objektu > Otevřete** příkaz **upravit** nabídky. Objekt se otevře v samostatném okně.

> [!NOTE]
>  Úpravy vložené položky v samostatném okně se standardní chování ve verzi 1 OLE a některé OLE – aplikace může podporovat jenom tento styl úprav.

Aktivace na místě podporuje zaměřené na dokument přístup k vytváření dokumentů. Uživatel může považovat za složeného dokumentu jedna entita, na něm pracovat bez nutnosti přepínat mezi aplikacemi. Aktivace na místě se ale používá pouze pro vložené položky, ne pro propojené položky: je nutné upravit v samostatném okně. Je to proto, že propojená položka je uložená ve skutečnosti na jiném místě. Úpravy propojená položka se provádí v rámci skutečné kontextu dat, to znamená, kde jsou data uložená. Úpravy propojená položka v samostatném okně upozorní uživatele, který data patří do jiného dokumentu.

MFC nepodporuje vnořené místní aktivace. Pokud vytvoříte aplikaci typu server/kontejner a, server/kontejner je vložen do jiného kontejneru a aktivaci, se nemůže místní aktivace objektů vložen dovnitř.

Co se stane vloženou položku, když uživatel poklepe to závisí na příkazy, které jsou definovány pro položku. Informace najdete v tématu [aktivace: Příkazy](../mfc/activation-verbs.md).

## <a name="see-also"></a>Viz také:

[OLE](../mfc/ole-in-mfc.md)<br/>
[Kontejnery](../mfc/containers.md)<br/>
[Servery](../mfc/servers.md)
