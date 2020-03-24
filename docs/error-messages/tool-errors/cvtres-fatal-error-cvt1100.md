---
title: Závažná chyba nástroje CVTRES CVT1100
ms.date: 11/04/2016
f1_keywords:
- CVT1100
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
ms.openlocfilehash: b7e67df24d41b1e8826673146fcc27fd93d143fd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196544"
---
# <a name="cvtres-fatal-error-cvt1100"></a>Závažná chyba nástroje CVTRES CVT1100

duplicitní prostředek – typ: typ, název: název, jazyk: jazyk, příznaky: příznaky, velikost: velikost

Zadaný prostředek byl zadán více než jednou.

Tato chyba se může zobrazit, pokud linker vytváří knihovnu typů a neurčili jste [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) a prostředek v projektu už používá 1. V takovém případě zadejte/TLBID a zadejte jiné číslo až 65535.
