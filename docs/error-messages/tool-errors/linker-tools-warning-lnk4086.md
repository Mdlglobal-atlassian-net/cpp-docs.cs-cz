---
title: Upozornění Linkerů LNK4086 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4086
dev_langs:
- C++
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21a2ee7660f0ad78d04f7edb191929296c8d47a9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079229"
---
# <a name="linker-tools-warning-lnk4086"></a>Upozornění linkerů LNK4086

vstupní bod 'function' není __stdcall s 'number' b argumentů; bitové kopie se možná nespustí.

Vstupní bod pro knihovnu DLL musí být `__stdcall`. Buď znovu zkompilovat funkci s [/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) možnost nebo zadejte `__stdcall` nebo WINAPI při definici funkce.