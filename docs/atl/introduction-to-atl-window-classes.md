---
title: Úvod do tříd oken ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window classes
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbd433eb024e7715c065a005ce06d38a086a5072
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765485"
---
# <a name="introduction-to-atl-window-classes"></a>Úvod do tříd oken ATL

Následující třídy ATL slouží k implementaci a manipulaci s windows:

- [Cwindow –](../atl/reference/cwindow-class.md) umožňuje připojit popisovač okna `CWindow` objektu. Poté je zapotřebí zavolat `CWindow` metody pro manipulaci s okna.

- [CWindowImpl](../atl/reference/cwindowimpl-class.md) umožňuje implementovat nové okno a zpracování zpráv s mapy zpráv. Můžete vytvořit okno založené na nové třídy, nadřazené třídu existující nebo podtřídy Windows existujícímu oknu.

- [CDialogImpl –](../atl/reference/cdialogimpl-class.md) umožňuje implementovat modální a nemodální dialogové okno pole a proces zprávy s mapy zpráv.

- [Ccontainedwindowt –](../atl/reference/ccontainedwindowt-class.md) je předem připravených třídu, která implementuje okno, jehož mapu zpráv je obsažen v jiné třídy. Pomocí `CContainedWindowT` umožňuje centralizovat zpracování zpráv v jedné třídě.

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) umožňuje implementovat dialogovému oknu (modálním nebo nemodálním), který je hostitelem ovládacích prvků ActiveX.

- [CSimpleDialog](../atl/reference/csimpledialog-class.md) umožňuje implementovat modální dialogové okno se základní funkčností.

- [Caxwindow –](../atl/reference/caxwindow-class.md) umožňuje implementovat okno, které hostuje ovládací prvek ActiveX.

- [Caxwindow2t –](../atl/reference/caxwindow2t-class.md) umožňuje implementovat okna, který je hostitelem licencovaného ovládacího prvku ActiveX.

Kromě tříd oken konkrétní knihovna ATL poskytuje několik tříd, které jsou navržené tak, aby implementace objektu ATL okno jednodušší. Jsou to tyto:

- [Cwndclassinfo –](../atl/reference/cwndclassinfo-class.md) spravuje informace o nové třídy okna.

- [Cwintraits –](../atl/reference/cwintraits-class.md) a [cwintraitsor –](../atl/reference/cwintraitsor-class.md) nabízejí jednoduchý způsob standardizovat vlastností objektu ATL okna.

## <a name="see-also"></a>Viz také

[Třídy oken](../atl/atl-window-classes.md)

