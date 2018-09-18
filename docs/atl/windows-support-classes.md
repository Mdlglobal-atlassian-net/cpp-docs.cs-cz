---
title: Windows podpůrných tříd (ATL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.windows
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9182241b1d33c63aae523cae0c2c9602466e4c2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090422"
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

## <a name="see-also"></a>Viz také

[Přehled tříd](../atl/atl-class-overview.md)<br/>
[Makra Map zpráv](../atl/reference/message-map-macros-atl.md)<br/>
[Makra třídy okna](../atl/reference/window-class-macros.md)

