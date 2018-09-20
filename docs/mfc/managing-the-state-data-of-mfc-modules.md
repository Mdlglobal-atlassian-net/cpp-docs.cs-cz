---
title: Správa údajů o stavu modulů knihovny MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- global state [MFC]
- data management [MFC], MFC modules
- window procedure entry points [MFC]
- exported interfaces and global state [MFC]
- module states [MFC], saving and restoring
- data management [MFC]
- MFC, managing state data
- multiple modules [MFC]
- module state restored [MFC]
ms.assetid: 81889c11-0101-4a66-ab3c-f81cf199e1bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1077128ec417ab0cd3e1fb0d5b7e57e1ffaec37
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442796"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>Správa údajů o stavu modulů knihovny MFC

Tento článek popisuje data o stavu modulů knihovny MFC a způsob, jakým je tento stav aktualizuje když dorazí opustí modulu toku provádění (cesta kód provede aplikace při spuštění). Přepíná stavy modulů s makry AFX_MANAGE_STATE a METHOD_PROLOGUE jsou také popsány.

> [!NOTE]
>  Termín "modul" zde odkazuje spustitelného programu nebo knihovny DLL (nebo sadu knihoven DLL), které budou fungovat nezávisle zbývajících částí aplikace, ale používá sdílené kopie knihovny MFC DLL. Ovládací prvek ActiveX je typickým příkladem modulu.

Jak je znázorněno na následujícím obrázku, knihovna MFC má data o stavu jednotlivých modulů použít v aplikaci. Mezi tato data patří například popisovače instance Windows (používané pro načítání prostředků), ukazatele na aktuální `CWinApp` a `CWinThread` objekty aplikace, počty odkazů modulu OLE a širokou škálu mapy, které udržují připojení mezi Obslužné rutiny a odpovídající instance objektů MFC objektů Windows. Ale když aplikace využívá více modulů, jsou data o stavu každého modulu, není aplikační široké. Místo toho každého modulu, který má vlastní soukromá kopie dat o stavu MFC.

![Stav data jeden modul &#40;aplikace&#41;](../mfc/media/vc387n1.gif "vc387n1") Data o stavu jednoho modulu (aplikace)

Data o stavu modulu je obsažen ve struktuře a je vždy k dispozici prostřednictvím ukazatele na danou strukturu. Tok provádění zadá konkrétního modulu, jak je znázorněno na následujícím obrázku, musí být stav tímto modulem stavu "aktuální" nebo "efektivní". Proto se každý objekt vlákna má ukazatel na strukturu efektivní stavu této aplikace. Udržování tento ukazatel aktualizován vůbec časy je důležité pro správu globální stav aplikace a zachování integrity stavu každého modulu. Nesprávný správy globální stav může způsobit nepředvídatelné chování aplikací.

![Stav data z více modulů](../mfc/media/vc387n2.gif "vc387n2") stavu dat více modulů

Každý modul jinými slovy, zodpovídá za správně přepínání mezi stavy modulů ve všech jeho vstupní body. "Vstupního bodu" je jakéhokoli místa, kde tok spouštění můžete zadat kód modulu. Vstupní body patří:

- [Exportované funkce v knihovně DLL](../mfc/exported-dll-function-entry-points.md)

- [Členské funkce rozhraní modelu COM](../mfc/com-interface-entry-points.md)

- [Procedury oken](../mfc/window-procedure-entry-points.md)

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)

