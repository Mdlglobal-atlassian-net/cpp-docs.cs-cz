---
title: Vytvoření aplikace knihovny MFC ve stylu Průzkumníka souborů
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcexplorer.project
helpviewer_keywords:
- browsers [MFC], Explorer-style applications
- MFC applications [MFC], Windows Explorer-style
- Explorer-style applications [MFC], creating
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
ms.openlocfilehash: 16969b7ef9c0447dfce971af8d329c5b93367041
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304883"
---
# <a name="creating-a-file-explorer-style-mfc-application"></a>Vytvoření aplikace knihovny MFC ve stylu Průzkumníka souborů

Mnoho aplikací systému Windows pomocí uživatelského rozhraní (UI) pro Průzkumníka souborů. Když spustíte Průzkumníka souborů, například se zobrazí aplikace s svislé příčky panelu dělení klientské oblasti. Levé straně od klientské oblasti obsahuje navigaci a procházení funkcí a pravému okraji oblasti klienta ukazuje podrobnosti o které jsou relevantní pro výběr v levém podokně. Po kliknutí na položku v levém podokně aplikace znovu naplní v pravém podokně. V aplikaci MDI, můžete použít příkazy na **zobrazení** změnit množství podrobností, které jsou uvedené v pravém podokně. (V aplikaci SDI nebo více dokumentů nejvyšší úrovně, můžete změnit podrobnosti, pomocí tlačítka panelu nástrojů.)

Obsah podokna závisí na aplikaci. V prohlížeči systému souborů v levém podokně nachází hierarchické zobrazení adresáře nebo počítače nebo skupiny počítačů, zatímco v pravém podokně se zobrazí složky, jednotlivé soubory, nebo počítače a informace o nich. Obsah nutně nemusí být soubory. Může být e-mailových zpráv, zpráv o chybách nebo jiné položky v databázi.

Průvodce vytvoří následující třídy:

- `CLeftView` Třída definuje podokno vlevo od klientské oblasti. Vždy je odvozen z [CTreeView](../../mfc/reference/ctreeview-class.md).

- C*název_projektu*zobrazení třídy definuje pravé podokno od klientské oblasti. Ve výchozím nastavení je odvozen z [CListView](../../mfc/reference/clistview-class.md) ale může být jiný typ zobrazení v závislosti na třídě zadáte z **základní třída** v seznamu [třídy generované v](../../mfc/reference/generated-classes-mfc-application-wizard.md) stránku Průvodce.

Generované aplikace může mít rozhraní jednoho dokumentu (SDI), rozhraní více dokumentů (MDI) nebo architekturu s více dokumentů na nejvyšší úrovni. Každé okno rámce aplikace vytvoří se svisle rozdělit pomocí [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md). Psaní kódu tohoto typu aplikace je podobný kódování běžné aplikace knihovny MFC, která používá rozdělovač, s tím rozdílem, že tento typ aplikace má samostatné zobrazení ovládacích prvků v rámci každé rozdělovač podokna.

Pokud používáte výchozí zobrazení seznamu v pravém podokně, Průvodce vytvoří další nabídce Možnosti (v pouze aplikace MDI) a tlačítka panelu nástrojů, chcete-li přepnout mezi velké ikony, malé ikony, seznamu a podrobností režimy zobrazení stylu.

### <a name="to-begin-creating-a-file-explorer-style-mfc-executable"></a>Můžete začít vytvářet spustitelný soubor stylem podobným Průzkumníku MFC

1. Postupujte podle pokynů v [vytvoření aplikace MFC](../../mfc/reference/creating-an-mfc-application.md).

1. V průvodci MFC aplikace [typ aplikace](../../mfc/reference/application-type-mfc-application-wizard.md) stránky, vyberte **Průzkumníka souborů** styl projektu.

1. Nastavte další možnosti, které očekáváte na dalších stránkách průvodce.

1. Klikněte na tlačítko **Dokončit** ke generování kostry aplikace.

Další informace naleznete v tématu:

- [Více typů dokumentů, zobrazení a oken s rámečkem](../../mfc/multiple-document-types-views-and-frame-windows.md)

- [Odvozené třídy zobrazení](../../mfc/derived-view-classes-available-in-mfc.md)

- [Volby při návrhu aplikací](../../mfc/application-design-choices.md)

## <a name="see-also"></a>Viz také:

[MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)<br/>
[Vytvoření aplikace MFC ve stylu webového prohlížeče](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)<br/>
[Vytvoření aplikace MFC založené na formulářích](../../mfc/reference/creating-a-forms-based-mfc-application.md)
