---
title: Kompilátor upozornění (úroveň 3) C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 56b27596296b87edcc6de406e7b6621d5723815d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402226"
---
# <a name="compiler-warning-level-3-c4192"></a>Kompilátor upozornění (úroveň 3) C4192

Při importu knihovny typů 'library' se automaticky vylučuje "name"

A `#import` knihovna obsahuje položky, *název*, která je také definováno v záhlaví systému Win32. Vzhledem k omezením z knihovny typů, názvy jako **IUnknown** nebo identifikátor GUID jsou často definovány v knihovně typů duplikování definice z hlavičky systému. `#import` zjistí tyto položky a odmítnout začlenit v souborech hlaviček .tlh a tli.

Chcete-li toto chování přepsat, použijte `#import` atributy [no_auto_exclude –](../../preprocessor/no-auto-exclude.md) a [include()](../../preprocessor/include-parens.md).