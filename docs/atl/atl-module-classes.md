---
title: ATL – třídy modulů
ms.date: 11/04/2016
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
ms.openlocfilehash: 2b72cac0da06b70a40e01fcc75da52f1678f3f64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317376"
---
# <a name="atl-module-classes"></a>ATL – třídy modulů

Toto téma popisuje třídy modulu, které byly nové v ATL 7.0.

## <a name="ccommodule-replacement-classes"></a>Třídy nahrazení modulu CComModule

Dřívější verze atl `CComModule`použité . V atl 7.0 `CComModule` funkce je nahrazen několika tříd:

- [Modul CAtlBase](../atl/reference/catlbasemodule-class.md) Obsahuje informace vyžadované většinou aplikací, které používají atl. Obsahuje HINSTANCE modulu a instance prostředku.

- [Modul CAtlCom](../atl/reference/catlcommodule-class.md) Obsahuje informace vyžadované třídami COM v atl.

- [Modul CAtlWin](../atl/reference/catlwinmodule-class.md) Obsahuje informace vyžadované windowing třídy v ATL.

- [CAtlDebugInterfacesModul](../atl/reference/catldebuginterfacesmodule-class.md) Obsahuje podporu pro ladění rozhraní.

- [Modul CAtl](../atl/reference/catlmodule-class.md) Následující `CAtlModule`odvozené třídy jsou přizpůsobeny tak, aby obsahovaly informace požadované v určitém typu aplikace. Většina členů v těchto třídách může být přepsána:

  - [CAtlDllModulT](../atl/reference/catldllmodulet-class.md) Používá se v aplikacích DLL. Poskytuje kód pro standardní exporty.

  - [CAtlExeModulT](../atl/reference/catlexemodulet-class.md) Používá se v aplikacích EXE. Poskytuje kód požadovaný v EXE.

  - [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) Poskytuje podporu pro vytváření služeb systému Windows NT a Windows 2000.

`CComModule`je stále k dispozici pro zpětnou kompatibilitu.

## <a name="reasons-for-distributing-ccommodule-functionality"></a>Důvody pro distribuci funkcí CComModule

Funkce `CComModule` aplikace byla rozdělena do několika nových tříd z následujících důvodů:

- Funkce můžete provést `CComModule` granulární.

   Podpora funkcí com, windowing, ladění rozhraní a specifických pro aplikaci (DLL nebo EXE) je nyní v samostatných třídách.

- Automaticky deklarovat globální instanci každého z těchto modulů.

   Globální instance požadovaných tříd modulu je propojena do projektu.

- Odeberte nutnost volání metod Init a Term.

   Init a Term metody byly přesunuty do konstruktory a destruktory pro třídy modulu; již není nutné volat Init a Term.

## <a name="see-also"></a>Viz také

[Koncepty](../atl/active-template-library-atl-concepts.md)<br/>
[Přehled třídy](../atl/atl-class-overview.md)
