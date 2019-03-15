---
title: Práce s vlákny modely a třídy kritických oddílů (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
ms.openlocfilehash: 98db15a1fee2637b9493b538468fa9446015404f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808154"
---
# <a name="threading-models-and-critical-sections-classes"></a>Práce s vlákny modely a třídy kritických oddílů

Následující třídy definují práce s vlákny modelu a kritický oddíl:

- [Catlautothreadmodule –](../atl/reference/catlautothreadmodule-class.md) implementuje ve fondu vláken, apartment model modelu COM serveru.

- [Catlautothreadmodulet –](../atl/reference/catlautothreadmodulet-class.md) poskytuje metody pro implementaci serveru ve fondu vláken, apartment model modelu COM.

- [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md) poskytuje bezpečným pro vlákno metody pro zvyšování a dekrementace proměnné. Obsahuje kritickou sekci.

- [Ccommultithreadmodelnocs –](../atl/reference/ccommultithreadmodelnocs-class.md) poskytuje bezpečným pro vlákno metody pro zvyšování a dekrementace proměnné. Neposkytuje kritický oddíl.

- [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md) poskytuje metody pro zvyšování a dekrementace proměnné. Neposkytuje kritický oddíl.

- [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel) určuje příslušné třídy modelu vláken pro jeden objekt třídy.

- [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel) určuje příslušné třídy modelu vláken pro objekt, který je globálně dostupná.

- [Ccomautocriticalsection –](../atl/reference/ccomautocriticalsection-class.md) obsahuje metody pro získání a uvolnění kritický oddíl. Kritický oddíl je automaticky inicializován.

- [Ccomautocriticalsection –](../atl/reference/ccomcriticalsection-class.md) obsahuje metody pro získání a uvolnění kritický oddíl. Kritický oddíl musí být explicitně inicializován.

- [Ccomfakecriticalsection –](../atl/reference/ccomfakecriticalsection-class.md) zrcadlí metody v `CComCriticalSection` bez zadání kritický oddíl. Metody v `CComFakeCriticalSection` Neprovádět žádnou akci.

- [Crtthreadtraits –](../atl/reference/crtthreadtraits-class.md) poskytuje funkce vytvoření vlákna CRT. Pokud vlákno použije funkce CRT, použijte tuto třídu.

- [Win32threadtraits –](../atl/reference/win32threadtraits-class.md) poskytuje funkce pro vytváření pro Windows vlákno. Pokud vlákno nebude používat funkce CRT, použijte tuto třídu.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../atl/atl-class-overview.md)
