---
title: Upozornění (úroveň 3) C4192 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4192
dev_langs:
- C++
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 671a8c83dcadcaa89372e53b6c3d677c5810b4a5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114407"
---
# <a name="compiler-warning-level-3-c4192"></a>Kompilátor upozornění (úroveň 3) C4192

Při importu knihovny typů 'library' se automaticky vylučuje "name"

A `#import` knihovna obsahuje položky, *název*, která je také definováno v záhlaví systému Win32. Vzhledem k omezením z knihovny typů, názvy jako **IUnknown** nebo identifikátor GUID jsou často definovány v knihovně typů duplikování definice z hlavičky systému. `#import` zjistí tyto položky a odmítnout začlenit v souborech hlaviček .tlh a tli.

Chcete-li toto chování přepsat, použijte `#import` atributy [no_auto_exclude –](../../preprocessor/no-auto-exclude.md) a [include()](../../preprocessor/include-parens.md).