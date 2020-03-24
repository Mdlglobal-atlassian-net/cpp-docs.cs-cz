---
title: Upozornění kompilátoru (úroveň 3) C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 38b346e0a90729bda431b9cb578a03806be1ea4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198975"
---
# <a name="compiler-warning-level-3-c4192"></a>Upozornění kompilátoru (úroveň 3) C4192

automaticky se vylučuje název při importu knihovny typů.

Knihovna `#import` obsahuje položku, *název*, která je také definována v hlavičkách systému Win32. Z důvodu omezení knihoven typů jsou názvy, jako je **IUnknown** nebo GUID, často definovány v knihovně typů a duplikují definici ze systémových hlaviček. `#import` zjistí tyto položky a odmítne je začlenit do souborů hlaviček. tlh a. tli.

Chcete-li toto chování přepsat, použijte `#import` atributy [no_auto_exclude](../../preprocessor/no-auto-exclude.md) a [include ()](../../preprocessor/include-parens.md).
