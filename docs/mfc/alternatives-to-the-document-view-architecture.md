---
title: Alternativy k architektuře Document / View | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07277e9b98186747415cf1bf6abed3e431e64fff
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403471"
---
# <a name="alternatives-to-the-documentview-architecture"></a>Alternativy k architektuře dokument/zobrazení

Aplikace MFC běžně používají architekturu document/view ke správě informací, formáty souborů a vizuální znázornění dat pro uživatele. Pro většinu aplikací klasické pracovní plochy architekturu document/view – architektura je taková, odpovídající a efektivní aplikace. Tato architektura rozděluje data ze zobrazení a ve většině případů, zjednodušuje vaší aplikace a snižuje redundantní kód.

Ale není vhodný v některých situacích architekturu document/view. Vezměte v úvahu tyto příklady:

- Pokud jsou přenesení aplikace napsané v jazyce C pro Windows, můžete chtít dokončit portů před přidáním document/view – podpora pro vaši aplikaci.

- Pokud píšete odlehčený nástroj, můžete zjistit, že můžete provést bez architekturu document/view.

- Pokud původní kód již používá Správa dat s daty zobrazení, přesunutí kódu do modelu dokument/zobrazení není vyplácet vzhledem k tomu, že je třeba oddělit pomocí dvou. Pravděpodobně budete chtít kód, jak je nechat.

Chcete-li vytvořit aplikaci, které nepoužívají architekturu document/view, zrušte **podpora architektury Document/View** zaškrtávací políčko v kroku 1 tohoto průvodce aplikací knihovny MFC. Zobrazit [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md) podrobnosti.

> [!NOTE]
>  Vytvořených pomocí Průvodce aplikací knihovny MFC aplikací založených na dialogovém okně nepoužívají architekturu document/view proto **podpora architektury Document/View** zaškrtávací políčko je zakázaná, pokud vyberete typ dialogového okna aplikace.

Průvodce Visual C++, stejně jako dialogové okno a zdroj editorů, pracovat s generované aplikace stejně jako jakékoli jiné aplikace generované v průvodci. Aplikace může podporovat panely nástrojů, posuvníky a stavový řádek a má **o** pole. Vaše aplikace nebude zaregistrována knihovna žádné šablony dokumentů a nesmí obsahovat třídy dokumentu.

Všimněte si, že generované aplikace obsahuje třídu zobrazení `CChildView`odvozenou z `CWnd`. Knihovna MFC vytvoří a umístí jednu instanci třídy zobrazení v rámci oken s rámečkem vytvořené vaší aplikace. MFC stále vynucuje použití okna zobrazení, protože zjednodušuje umístění a správu obsahu vaší aplikace. Můžete přidat kód vykreslení obsahu `OnPaint` členy této třídy. Váš kód by měl přidat posuvníky zobrazení, nikoli rámce.

Protože architekturu document/view k dispozici v prostředí MFC je zodpovědná za implementaci mnoha základních funkcí aplikace, neexistuje ve vašem projektu znamená, že, zodpovídáte za implementaci mnoha důležitých funkcí vaší aplikace:

- Podle Průvodce aplikací MFC, v nabídce pro vaše aplikace obsahuje jenom **nový** a **ukončovací** příkazy na **souboru** nabídky. ( **Nový** příkaz je podporován pouze pro aplikace MDI, podporu není aplikace SDI bez Document/View.) Prostředek generované nabídky nebude podporovat seznamu naposledy použitých (naposledy použité).

- Je nutné přidat funkce obslužné rutiny a implementace pro všechny příkazy, které bude vaše aplikace podporovat, včetně **otevřít** a **Uložit** na **souboru** nabídky. Knihovna MFC poskytuje běžně kódu, který podporuje tyto funkce, ale tato podpora je úzce vázán k architektuře dokument/zobrazení.

- Panel nástrojů pro vaši aplikaci, pokud jste požádali o jeden, bude minimální.

Důrazně doporučujeme použít Průvodce aplikací knihovny MFC k vytváření aplikací bez architekturu document/view Průvodce zaručuje správnou architektury MFC. Nicméně pokud je třeba se vyvarovat použití průvodce, tady je několik přístupů pro obcházení architekturu document/view ve vašem kódu:

- Považovat za nepoužívané appendage dokumentu a implementujte kód pro správu vašich dat ve třídě zobrazení, jak je navrženo výše. Režie pro dokument je relativně nízký. Jediný [CDocument](../mfc/reference/cdocument-class.md) objektu s sebou nese náklady malé množství režie samostatně a navíc malé nároky na `CDocument`od základních tříd, [CCmdTarget –](../mfc/reference/ccmdtarget-class.md) a [CObject](../mfc/reference/cobject-class.md). I ten, že třídy jsou malé.

     Deklarované v `CDocument`:

   - Dvě `CString` objekty.

   - Tři **BOOL**s.

   - Jeden `CDocTemplate` ukazatele.

   - Jeden `CPtrList` objektu, který obsahuje seznam zobrazení dokumentu.

     Kromě toho dokumentů vyžaduje základní množství času vytvořit objekt dokumentu, jeho zobrazení objektů, okno rámce a objekt šablony dokumentu.

- Považovat za dokument a zobrazení postranní nepoužité řetězce. Vložte kód pro vykreslování a správy dat v okně rámce místo zobrazení. Tento přístup je blíž ke jazyka C programovací model.

- Přepište částí rozhraní MFC, které vytvoří dokument a zobrazení k odstranění všech jejich vytváření. Proces vytvoření dokumentu začíná volání `CWinApp::AddDocTemplate`. Odstranit toto volání z třídy aplikace `InitInstance` členské funkce a místo toho vytvořit v okně s rámečkem `InitInstance` sami. Ukládejte kód data správy vaší třídy oken s rámečkem. V procesu vytváření dokumentů/zobrazení je znázorněn v [vytváření dokumentů/zobrazení](../mfc/document-view-creation.md). To představuje víc práce a vyžaduje hlubší porozumění rozhraní framework, ale umožní vám zcela z dokumentů/zobrazení režii.

Článek [knihovny MFC: použití třídy databáze bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md) konkrétnější příklady alternativy dokument/zobrazení v rámci databázové aplikace.

## <a name="see-also"></a>Viz také

[Document/View – architektura](../mfc/document-view-architecture.md)

