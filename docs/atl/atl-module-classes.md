---
title: ATL – třídy modulů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af9749e2809678a7d7a8cc1e2bc6f4c2a40fbd6a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753461"
---
# <a name="atl-module-classes"></a>ATL – třídy modulů

Toto téma popisuje třídy modulů, které byly v ATL 7.0.

## <a name="ccommodule-replacement-classes"></a>Ccommodule – nahrazení tříd

Starší verze knihovny ATL použity `CComModule`. V ATL 7.0 `CComModule` funkci nahrazuje několik tříd:

- [Catlbasemodule –](../atl/reference/catlbasemodule-class.md) obsahuje informace potřebné pro většinu aplikace, které používají knihovnu ATL. Obsahuje HINSTANCE modulu a instance prostředků.

- [Catlcommodule –](../atl/reference/catlcommodule-class.md) obsahuje informace potřebné v rámci tříd modelu COM v knihovně ATL

- [Catlwinmodule –](../atl/reference/catlwinmodule-class.md) obsahuje informace potřebné v rámci tříd oken v knihovně ATL

- [Catldebuginterfacesmodule –](../atl/reference/catldebuginterfacesmodule-class.md) obsahuje podporu pro ladění v rozhraní.

- [Catlmodule –](../atl/reference/catlmodule-class.md) následující `CAtlModule`– obsahuje informace potřebné v konkrétní aplikaci typu jsou přizpůsobeny odvozené třídy. Většina členové těchto tříd lze přepsat:

   - [Catldllmodulet –](../atl/reference/catldllmodulet-class.md) použít v aplikacích knihovny DLL. Poskytuje kód pro standardní export.

   - [Catlexemodulet –](../atl/reference/catlexemodulet-class.md) použít v aplikacích EXE. Poskytuje kód vyžaduje EXE.

   - [Catlservicemodulet –](../atl/reference/catlservicemodulet-class.md) poskytuje podporu pro vytvoření služeb Windows 2000 a Windows NT.

`CComModule` je stále k dispozici z důvodu zpětné kompatibility.

## <a name="reasons-for-distributing-ccommodule-functionality"></a>Důvody pro distribuci ccommodule – funkce

Funkce `CComModule` byl distribuován do nové třídy několik z následujících důvodů:

- Ujistěte se, funkce v `CComModule` podrobné.

     Podpora COM, časová okna, ladění v rozhraní a funkce (knihovna DLL nebo EXE) specifické pro aplikaci je nyní v samostatné třídy.

- Automaticky deklarujte globální instance každé z těchto modulů.

     Globální instanci třídy vyžaduje modul je do projektu propojen.

- Odeberte nutnost volání metody Init a délku smlouvy.

     Metody Init a termín bylo přesunuto do konstruktory a destruktory pro modul třídy; již není potřeba volat Init a délku smlouvy.

## <a name="see-also"></a>Viz také

[Koncepty](../atl/active-template-library-atl-concepts.md)   
[Přehled tříd](../atl/atl-class-overview.md)

