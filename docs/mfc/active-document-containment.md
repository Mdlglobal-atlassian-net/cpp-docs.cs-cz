---
title: Práce s kontejnery aktivních dokumentů
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
ms.openlocfilehash: dc13384454c4732d3efbf99def5d05dd4f2d44aa
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776567"
---
# <a name="active-document-containment"></a>Práce s kontejnery aktivních dokumentů

Zahrnutí aktivního dokumentu je technologie, která poskytuje jeden snímek, ve kterém chcete pracovat s dokumenty, místo vynucení můžete vytvářet a používat více aplikací snímků pro každý typ dokumentu. Se liší od základních technologií OLE v tom, že OLE funguje s objekty vložené do složeného dokumentu, ve kterém může být aktivní jenom jednoduchým obsahem. V případě zahrnutí aktivního dokumentu aktivovat celý dokument (tedy celou aplikaci, včetně přidružených nabídky, panely nástrojů a tak dále) v rámci kontextu jeden snímek.

Technologie zahrnutí aktivního dokumentu původně vyvinutý pro Microsoft Office pro implementaci modul vazby sady Office. Nicméně tato technologie je dostatečně flexibilní, aby podporují kontejnery pro aktivní dokument než modul vazby sady Office a může podporovat servery dokumenty než aplikace Office a kompatibilní se sadou Office.

Aplikace, který je hostitelem aktivní dokumenty je volána [kontejner pro aktivní dokument](../mfc/active-document-containers.md). Příklady takových kontejnerů: modul vazby sady Office Microsoft nebo Microsoft Internet Explorer.

Zahrnutí aktivního dokumentu je implementován jako sada rozšíření OLE – dokumenty, složeného dokumentu technologie OLE. Rozšíření jsou další rozhraní, které umožňují Vložitelný, místní objekt představující celý dokument místo jednoduchým vloženého obsahu. Stejně jako u dokumenty OLE, zahrnutí aktivního dokumentu používá kontejner, který poskytuje prostor pro zobrazení pro aktivní dokumenty a servery, které poskytují rozhraní a manipulaci s možností uživatele pro aktivní dokumenty sami.

[Server pro aktivní dokument](../mfc/active-document-servers.md) je aplikace (například Word, Excel nebo PowerPoint), která podporuje jednu nebo více tříd aktivního dokumentu, kde každý samotného objektu podporuje rozšíření rozhraní, které umožňují objekt, který má být aktivován v vhodné kontejneru.

[Aktivní dokument](../mfc/active-documents.md) (k dispozici z aktivního dokumentu serveru jako je například aplikaci Word nebo Excel) je v podstatě plnohodnotnému, konvenční dokument, který je vložený jako objekt v rámci jiný kontejner pro aktivní dokument. Na rozdíl od vložené objekty aktivní dokumenty Získejte úplnou kontrolu nad jejich stránky a je k dispozici pro uživatele, aby upravovat úplné rozhraní aplikace (pomocí všechny jeho základní příkazy a nástroje).

Aktivní dokument je nejlepší srozumitelné odlišující jej od standardní vloženého objektu OLE. Následující konvence OLE vložený objekt je takový, který se zobrazí v rámci stránky dokumentu, který ho vlastní a spravuje dokumentu kontejneru OLE. Kontejner ukládá data vloženého objektu s zbývající části dokumentu. Vložené objekty jsou však omezeny v tom, že nemají vliv na stránku, na kterém jsou uvedeny.

Uživatelé aplikace kontejnerů pro aktivní dokument můžete vytvořit aktivní dokumenty (označované jako oddíly v modul vazby sady Office) používání jejich oblíbených aplikací (za předpokladu, že tyto aplikace jsou aktivní dokument povoleno), ale uživatelů můžete spravovat jako výsledný projekt jedna entita, která může být jedinečně pojmenovaná, uložit, tisk, a tak dále. Stejným způsobem můžete uživatele internetovém prohlížeči považovat celá síť, jakož i místní systémy souborů, jako entita úložiště jednotlivý dokument s možností procházet dokumenty v tomto úložišti z jednoho místa.

## <a name="sample-programs"></a>Ukázkové aplikace

- [MFCBIND](../overview/visual-cpp-samples.md) ukázka ilustruje implementaci aplikace kontejnerů pro aktivní dokument.

## <a name="see-also"></a>Viz také:

[MFC COM](../mfc/mfc-com.md)
