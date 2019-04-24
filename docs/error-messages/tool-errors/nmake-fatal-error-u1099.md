---
title: Závažná chyba nástroje NMAKE U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: 395f25d8d27bc5e9b6132c87390c8c3bc19b6cc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298240"
---
# <a name="nmake-fatal-error-u1099"></a>Závažná chyba nástroje NMAKE U1099

přetečení zásobníku

Zpracování souboru pravidel byla příliš složitý pro aktuální přidělení zásobníku v nástroji NMAKE. NMAKE má přidělený objem 0x3000 (12 kb / s).

Pro zvýšení přidělení zásobníku v NMAKE, spusťte [/Stack editbin](../../build/reference/stack.md) nástroj s větší možností zásobníku:

**Editbin – /STACK:reserve NMAKE. SOUBOR EXE**

kde *rezervovat* je větší než aktuální přidělení zásobníku v nástroji NMAKE číslo.