---
title: Třídy architektury aplikace MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
ms.openlocfilehash: 1e09447623b32e9b10063af5bc91ac9589f45e44
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447717"
---
# <a name="mfc-application-architecture-classes"></a>Třídy architektury aplikace MFC

Třídy v této kategorii přispívají k architektuře aplikace architektury. Poskytují funkce společné pro většinu aplikací. Vyplníte rozhraní a přidáte funkce specifické pro aplikaci. Obvykle to provedete odvozením nových tříd z tříd architektury a následným přidáním nových členů nebo přepsáním existujících členských funkcí.

[Průvodci aplikací](../mfc/reference/mfc-application-wizard.md) generují několik typů aplikací, přičemž všechny používají aplikační rozhraní různými způsoby. Aplikace SDI (Single Document Interface) a MDI (více dokumentů rozhraní) plně využívají část rozhraní s názvem architektura Document/View. Jiné typy aplikací, jako jsou například aplikace založené na dialogových oknech, formulářové aplikace a knihovny DLL, používají pouze některé funkce architektury Document/View.

Aplikace Document/View obsahují jednu nebo více sad dokumentů, zobrazení a oken s rámečkem. Objekt šablony dokumentu přidruží třídy pro jednotlivé sady dokumentů, zobrazení a snímků.

I když v aplikaci MFC nemusíte používat architekturu dokument/zobrazení, existuje několik výhod, jak to provést. Podpora kontejnerů a serverů knihovny MFC technologie OLE je založena na architektuře document/view, protože je podpora pro tisk a náhled tisku.

Všechny aplikace MFC mají alespoň dva objekty: aplikační objekt odvozený z [CWinApp](../mfc/reference/cwinapp-class.md)a nějaký druh objektu hlavního okna, který je odvozen (často nepřímo) z [CWnd](../mfc/reference/cwnd-class.md). (Nejčastěji je hlavní okno odvozeno z [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd –](../mfc/reference/cmdiframewnd-class.md)nebo [CDialog](../mfc/reference/cdialog-class.md), z nichž všechny jsou odvozeny z `CWnd`.)

Aplikace, které používají architekturu document/view, obsahují další objekty. Hlavní objekty jsou:

- Aplikační objekt odvozený od třídy [CWinApp](../mfc/reference/cwinapp-class.md), jak je uvedeno výše.

- Jeden nebo více objektů třídy dokumentu odvozených ze třídy [objektu CDocument](../mfc/reference/cdocument-class.md). Objekty tříd dokumentu zodpovídají za interní reprezentace dat, která jsou v zobrazení manipulována. Mohou být přidruženy k datovému souboru.

- Jeden nebo více objektů zobrazení odvozených z třídy [CView](../mfc/reference/cview-class.md). Každé zobrazení je okno, které je připojeno k dokumentu a je spojeno s oknem rámce. Zobrazení zobrazení a manipulace s daty obsaženými v objektu třídy dokumentu.

Aplikace Document/View obsahují také okna s rámečkem (odvozená z [CFrameWnd](../mfc/reference/cframewnd-class.md)) a šablony dokumentů (odvozené z [CDocTemplate –](../mfc/reference/cdoctemplate-class.md)).

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
