---
title: Závažná chyba nástroje CVTRES CVT1100 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CVT1100
dev_langs:
- C++
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18a5508301c54637fb34a751c8f1c4e307e47d50
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068959"
---
# <a name="cvtres-fatal-error-cvt1100"></a>Závažná chyba nástroje CVTRES CVT1100

duplicitní prostředek – typu: typ, název: název, jazyk: jazyk, příznaky: příznaky, size: velikost

Daný prostředek byl zadán více než jednou.

Této chybě může dojít, pokud linker vytváří knihovnu typů a nezadali jste [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) a prostředků v projektu již používá 1. V takovém případě zadejte /TLBID a zadejte jiné číslo až 65535.