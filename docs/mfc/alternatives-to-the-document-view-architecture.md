---
title: Alternativy k architektuře zobrazení dokumentů
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
ms.openlocfilehash: 41af30d25d7ddb9e2bdbb7a0f7b86cb741ae1048
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370791"
---
# <a name="alternatives-to-the-documentview-architecture"></a>Alternativy k architektuře dokument/zobrazení

Aplikace knihovny MFC obvykle používají architekturu dokumentu/zobrazení ke správě informací, formátů souborů a vizuální reprezentace dat uživatelům. Pro většinu desktopových aplikací je architektura dokumentu/zobrazení vhodnou a efektivní architekturou aplikací. Tato architektura odděluje data od zobrazení a ve většině případů zjednodušuje aplikaci a snižuje redundantní kód.

Architektura dokumentu/zobrazení však není vhodná pro některé situace. Vezměme si tyto příklady:

- Pokud přepojíte aplikaci napsanou v c pro Systém Windows, můžete před přidáním podpory dokumentu nebo zobrazení do aplikace dokončit port.

- Pokud píšete lehký nástroj, můžete zjistit, že můžete provést bez architektury dokumentu nebo zobrazení.

- Pokud váš původní kód již kombinuje správu dat se zobrazením dat, přesunutí kódu do modelu dokumentu nebo zobrazení nestojí za námahu, protože je nutné oddělit tyto dva. Možná byste raději ponechat kód tak, jak je.

Chcete-li vytvořit aplikaci, která nepoužívá architekturu dokumentu/zobrazení, zrušte zaškrtnutí políčka **Podpora architektury dokument/zobrazení** v kroku 1 Průvodce aplikací knihovny MFC. Podrobnosti naleznete v [Průvodci aplikací knihovny MFC.](../mfc/reference/mfc-application-wizard.md)

> [!NOTE]
> Aplikace založené na dialogu vytvořené Průvodcem aplikací knihovny MFC nepoužívají architekturu dokumentu nebo zobrazení, takže pokud vyberete typ aplikace dialogového okna, je zaškrtávací políčko **Podpora architektury dokument/zobrazení** zakázáno.

Průvodci visual c++, stejně jako zdrojové a dialogové editory, pracují s vygenerovanou aplikací stejně jako u jiných aplikací generovaných Průvodcem. Aplikace podporuje panely nástrojů, posuvníky a stavový řádek a má pole **O.** Aplikace nebude registrovat žádné šablony dokumentů a nebude obsahovat třídu dokumentu.

Všimněte si, že vaše generované `CChildView`aplikace má `CWnd`třídu zobrazení, , odvozené z . Knihovna MFC vytvoří a umístí jednu instanci třídy zobrazení v rámci oken vytvořených vaší aplikací. Knihovna MFC stále vynucuje pomocí okna zobrazení, protože zjednodušuje umístění a správu obsahu aplikace. Do `OnPaint` člena této třídy můžete přidat kód malování. Váš kód by měl přidat posuvníky do zobrazení, nikoli do rámce.

Vzhledem k tomu, že architektura dokumentu/zobrazení poskytovaná knihovnou MFC je zodpovědná za implementaci mnoha základních funkcí aplikace, její absence v projektu znamená, že jste zodpovědní za implementaci mnoha důležitých funkcí aplikace:

- Podle Průvodce aplikací knihovny MFC obsahuje nabídka pro vaši aplikaci v nabídce **Soubor** pouze příkazy **Nový** a **Ukončit.** (Příkaz **Nový** je podporován pouze pro aplikace MDI, nikoli pro aplikace SDI bez podpory dokumentu/zobrazení.) Vygenerovaný prostředek nabídky nebude podporovat seznam NAPOSLEDY POUŽITÝCH položek (naposledy použitý).

- Je nutné přidat obslužné rutiny funkce a implementace pro všechny příkazy, které vaše aplikace bude podporovat, včetně **Otevřít** a **Uložit** na **soubor** menu. Knihovna MFC obvykle poskytuje kód pro podporu těchto funkcí, ale tato podpora je pevně vázána na architekturu dokumentu nebo zobrazení.

- Panel nástrojů pro vaši aplikaci, pokud jste o ni požádali, bude minimální.

Důrazně doporučujeme použít Průvodce aplikací knihovny MFC k vytvoření aplikací bez architektury dokumentu nebo zobrazení, protože průvodce zaručuje správnou architekturu knihovny MFC. Pokud se však musíte vyhnout použití průvodce, zde je několik přístupů pro vynechání architektury dokumentu nebo zobrazení v kódu:

- Považovat dokument za nevyužitý přílohu a implementovat kód správy dat ve třídě zobrazení, jak je navrženo výše. Režie pro dokument je relativně nízká. Jeden [cdocument](../mfc/reference/cdocument-class.md) objekt unese malé množství režie sám o `CDocument`sobě, plus malé režii 's základní třídy [CCmdTarget](../mfc/reference/ccmdtarget-class.md) a [CObject](../mfc/reference/cobject-class.md). Obě posledně uvedené třídy jsou malé.

   Prohlášení `CDocument`v :

  - Dva `CString` objekty.

  - Tři **BOOL**s.

  - Jeden `CDocTemplate` ukazatel.

  - Jeden `CPtrList` objekt, který obsahuje seznam zobrazení dokumentu.

  Dokument navíc vyžaduje dobu k vytvoření objektu dokumentu, jeho objektů zobrazení, okna rámce a objektu šablony dokumentu.

- Považovat dokument i zobrazení za nepoužívané přílohy. Místo zobrazení vložte správu dat a kód výkresu do okna rámce. Tento přístup je blíže k programovacímu modelu jazyka C.

- Přepište části architektury knihovny MFC, které vytvářejí dokument a zobrazení eliminovat jejich vytváření vůbec. Proces vytváření dokumentu začíná voláním `CWinApp::AddDocTemplate`aplikace . Odstraňte toto volání z `InitInstance` členské funkce vaší třídy aplikace `InitInstance` a místo toho vytvořte okno rámce v sobě. Vložte kód správy dat do třídy okna rámce. Proces vytváření dokumentu/zobrazení je znázorněn v [dokumentu/zobrazení .](../mfc/document-view-creation.md) To je více práce a vyžaduje hlubší pochopení rámce, ale uvolní zcela dokumentu/zobrazení režie.

Článek [Knihovny MFC: Použití tříd databáze bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md) poskytuje konkrétnější příklady alternativ dokumentu/zobrazení v kontextu databázových aplikací.

## <a name="see-also"></a>Viz také

[Architektura dokumentu/zobrazení](../mfc/document-view-architecture.md)
