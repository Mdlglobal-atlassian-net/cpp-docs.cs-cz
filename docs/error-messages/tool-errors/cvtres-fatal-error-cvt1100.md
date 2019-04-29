---
title: Závažná chyba nástroje CVTRES CVT1100
ms.date: 11/04/2016
f1_keywords:
- CVT1100
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
ms.openlocfilehash: c7e65ccc79852ec99dd2406398fe1b3cdecacde7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406272"
---
# <a name="cvtres-fatal-error-cvt1100"></a>Závažná chyba nástroje CVTRES CVT1100

duplicitní prostředek – typu: typ, název: název, jazyk: jazyk, příznaky: příznaky, size: velikost

Daný prostředek byl zadán více než jednou.

Této chybě může dojít, pokud linker vytváří knihovnu typů a nezadali jste [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) a prostředků v projektu již používá 1. V takovém případě zadejte /TLBID a zadejte jiné číslo až 65535.