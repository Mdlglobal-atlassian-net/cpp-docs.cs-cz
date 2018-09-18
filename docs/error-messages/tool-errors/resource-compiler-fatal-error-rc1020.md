---
title: Závažná chyba kompilátoru prostředků RC1020 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1020
dev_langs:
- C++
helpviewer_keywords:
- RC1020
ms.assetid: 3e073ebf-9136-4bf8-ac6a-3c642ed64594
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe19b079a0407f07796bd8141db2cbedaf02cbbb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032962"
---
# <a name="resource-compiler-fatal-error-rc1020"></a>Závažná chyba kompilátoru prostředků RC1020

neočekávané "#endif.

`#endif` Směrnice zobrazovaly bez odpovídajícího `#if`, **#ifdef**, nebo **#ifndef** směrnice.

Ujistěte se, že existuje odpovídající `#endif` pro každou `#if`, **#ifdef**, a **#ifndef** příkazu.