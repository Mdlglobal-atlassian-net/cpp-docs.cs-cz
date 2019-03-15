---
title: Přidání nového rozhraní projektu ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.interface
helpviewer_keywords:
- interfaces, adding to ATL objects
- Implement Interface ATL wizard
- controls [ATL], interfaces
- ATL projects, adding interfaces
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
ms.openlocfilehash: 99f262d420cd503c6ca385ed29bcaa2647c5f556
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810052"
---
# <a name="adding-a-new-interface-in-an-atl-project"></a>Přidání nového rozhraní projektu ATL

Přidat rozhraní do objektu nebo ovládací prvek, vytvoříte prázdná funkce pro jednotlivé metody v tomto rozhraní. V objektu nebo ovládací prvek lze přidat pouze rozhraní, které jsou aktuálně součástí existující knihovnu typů. Kromě toho musí implementovat třídu, ve kterém můžete přidat rozhraní [BEGIN_COM_MAP](com-map-macros.md#begin_com_map) – makro nebo, pokud je projekt s atributy, musí mít `coclass` atribut.

Nové rozhraní můžete přidat do vašeho ovládacího prvku v jednom ze dvou způsobů: ručně nebo pomocí průvodců kódem v zobrazení tříd.

## <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>Přidat rozhraní do existujícího objektu nebo ovládací prvek pomocí průvodců kódem v zobrazení tříd

1. V [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na název třídy ovládacího prvku. Například Úplné řízení nebo složených ovládacích prvků nebo jiných, který implementuje BEGIN_COM_MAP maker v souboru hlaviček třídy ovládacího prvku.

1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **implementovat rozhraní**.

1. Vyberte rozhraní k implementaci v [implementovat rozhraní průvodce](../../ide/implement-interface-wizard.md). Pokud rozhraní neexistuje v libovolné dostupné knihovny typů, pak jste musí jej ručně přidat do souboru IDL.

## <a name="to-add-a-new-interface-manually"></a>Chcete-li ručně přidat nové rozhraní

1. Přidejte definici nového rozhraní do souboru IDL.

1. Odvození objektu nebo ovládací prvek z rozhraní.

1. Vytvořte nový [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) rozhraní nebo, pokud je projekt s atributy, přidejte `coclass` atribut.

1. Implementace metody v rozhraní.

## <a name="see-also"></a>Viz také:

[Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Typy projektů Visual C++](../../build/reference/visual-cpp-project-types.md)<br/>
[Programování s použitím knihovny ATL a běhového kódu jazyka C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Základy ATL – objekty COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)
