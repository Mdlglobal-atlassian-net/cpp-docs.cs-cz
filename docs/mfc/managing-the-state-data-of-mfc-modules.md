---
title: Správa údajů o stavu modulů knihovny MFC
ms.date: 11/19/2018
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
ms.openlocfilehash: c8e79f54ed586201a7d82327662643a9a241b8f4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357271"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>Správa údajů o stavu modulů knihovny MFC

Tento článek popisuje data stavu modulů knihovny MFC a jak je tento stav aktualizován, když tok spuštění (kód cesty prochází aplikací při provádění) zadá a opustí modul. Přepnutí stavů modulu s AFX_MANAGE_STATE a METHOD_PROLOGUE makra je také diskutována.

> [!NOTE]
> Termín "modul" zde odkazuje na spustitelný program nebo knihovnu DLL (nebo sadu knihoven DLL), které pracují nezávisle na zbytku aplikace, ale používají sdílenou kopii knihovny MFC DLL. Ovládací prvek ActiveX je typickým příkladem modulu.

Jak je znázorněno na následujícím obrázku, knihovna MFC obsahuje data stavu pro každý modul použitý v aplikaci. Příklady těchto dat zahrnují popisovače instancí systému Windows `CWinApp` (používané pro načítání prostředků), ukazatele na aktuální a `CWinThread` objekty aplikace, počty odkazů modulu OLE a různé mapy, které udržují připojení mezi popisovači objektů systému Windows a odpovídajícími instancemi objektů knihovny MFC. Pokud však aplikace používá více modulů, stavová data každého modulu nejsou širokou aplikací. Místo toho každý modul má vlastní soukromou kopii dat stavu knihovny MFC.

![Stavová data jednoho modulu &#40;aplikace&#41;](../mfc/media/vc387n1.gif "Stavová data jednoho modulu &#40;aplikace&#41;") <br/>
Stavová data jednoho modulu (aplikace)

Data stavu modulu je obsažena ve struktuře a je vždy k dispozici prostřednictvím ukazatele na tuto strukturu. Když tok provádění zadá konkrétní modul, jak je znázorněno na následujícím obrázku, stav tohoto modulu musí být "aktuální" nebo "efektivní" stav. Proto každý objekt podprocesu má ukazatel na strukturu efektivní stav této aplikace. Udržování tohoto ukazatele aktualizovány po celou dobu je důležité pro správu globálního stavu aplikace a zachování integrity stavu každého modulu. Nesprávná správa globálního stavu může vést k nepředvídatelnému chování aplikace.

![Stavová data více modulů](../mfc/media/vc387n2.gif "Stavová data více modulů") <br/>
Stavová data více modulů

Jinými slovy, každý modul je zodpovědný za správné přepínání mezi stavy modulu na všech vstupních bodech. "Vstupní bod" je jakékoli místo, kde tok provádění můžete zadat kód modulu. Vstupní body zahrnují:

- [Exportované funkce v dll](../mfc/exported-dll-function-entry-points.md)

- [Členské funkce rozhraní COM](../mfc/com-interface-entry-points.md)

- [Procedury oken](../mfc/window-procedure-entry-points.md)

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)
