---
title: Chyba kompilátoru C2856 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2856
dev_langs:
- C++
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df6226bfd2fc11f05f894091f4ff02c145d09e11
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072708"
---
# <a name="compiler-error-c2856"></a>Chyba kompilátoru C2856

\#hdrstop – Direktiva pragma nemůže být uvnitř bloku #if.

`hdrstop` – Direktiva pragma nelze umístit uvnitř těla bloku podmíněné kompilace.

Přesunout `#pragma hdrstop` příkazu, který není obsažen v oblasti `#if/#endif` bloku.