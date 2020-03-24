---
title: Závažná chyba nástroje NMAKE U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: c963180059a48d9aa0b09103df1ed54f82b8a2f1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193391"
---
# <a name="nmake-fatal-error-u1099"></a>Závažná chyba nástroje NMAKE U1099

přetečení zásobníku

Zpracování souboru pravidel bylo pro aktuální přidělení zásobníku v nástroji NMAKE příliš složité. NMAKE má přidělení 0x3000 (12K).

Chcete-li zvýšit alokaci zásobníku nástroje NMAKE, spusťte nástroj [nástroje EDITBIN/Stack](../../build/reference/stack.md) s větší možností zásobníku:

**nástroje EDITBIN/STACK: vyhradit NMAKE PROGRAMU**

kde *rezerva* je číslo větší než aktuální přidělení zásobníku v nástroji NMAKE.
