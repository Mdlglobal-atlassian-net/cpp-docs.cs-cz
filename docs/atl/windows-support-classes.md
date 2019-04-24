---
title: Třídy podpory Windows (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
ms.openlocfilehash: 5880fd970d885da84edd94f9f2c7a47ec326ebe1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195478"
---
# <a name="windows-support-classes"></a>Třídy podpory Windows

Následující třídy poskytují podporu pro windows:

- [_U_menuorid –](../atl/reference/u-menuorid-class.md) poskytuje obálky pro `CreateWindow` a `CreateWindowEx`.

- [Cwindow –](../atl/reference/cwindow-class.md) obsahuje metody pro práci s časového období. `CWindow` je základní třídou pro `CWindowImpl`, `CDialogImpl`, a `CContainedWindow`.

- [CWindowImpl](../atl/reference/cwindowimpl-class.md) implementuje okno založené na nové třídě okna. Také vám umožní podtřídy nebo nadřazené třídy okna.

- [CDialogImpl –](../atl/reference/cdialogimpl-class.md) implementuje dialog.

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) implementuje dialogovému oknu (modálním nebo nemodálním), který je hostitelem ovládacích prvků ActiveX.

- [CSimpleDialog](../atl/reference/csimpledialog-class.md) implementuje dialog (modálním nebo nemodálním) se základní funkčností.

- [Caxwindow –](../atl/reference/caxwindow-class.md) manipuluje okno, které hostuje ovládací prvek ActiveX.

- [Caxwindow2t –](../atl/reference/caxwindow2t-class.md) poskytuje metody pro práci s okno, které hostuje ovládací prvek ActiveX a také zahrnuje podporu pro hostování licencované ovládací prvky ActiveX.

- [Ccontainedwindowt –](../atl/reference/ccontainedwindowt-class.md) implementuje oken obsažených v rámci jiného objektu.

- [Cwndclassinfo –](../atl/reference/cwndclassinfo-class.md) spravuje informace o nové třídy okna.

- [Cdynamicchain –](../atl/reference/cdynamicchain-class.md) podporuje dynamické řetězení mapy zpráv.

- [Cmessagemap –](../atl/reference/cmessagemap-class.md) umožňuje objektu vystavit její zprávy se mapuje na jiné objekty.

- [Cwintraits –](../atl/reference/cwintraits-class.md) poskytuje jednoduchý způsob standardizovat vlastností objektu ATL okna.

- [Cwintraitsor –](../atl/reference/cwintraitsor-class.md) poskytuje výchozí hodnoty pro styly oken a rozšířené stylů použitých k vytvoření okna. Tyto hodnoty jsou přidány pomocí operátoru logický operátor OR na hodnoty, které jsou k dispozici při vytváření okna.

## <a name="related-articles"></a>Související články

[ATL – třídy oken](../atl/atl-window-classes.md)

[ATL – tutoriál](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Viz také:

[Přehled tříd](../atl/atl-class-overview.md)<br/>
[Makra Map zpráv](../atl/reference/message-map-macros-atl.md)<br/>
[Makra třídy okna](../atl/reference/window-class-macros.md)
