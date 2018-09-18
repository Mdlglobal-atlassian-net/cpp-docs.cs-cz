---
title: Závažná chyba nástroje NMAKE U1099 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1099
dev_langs:
- C++
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3ef75a1435d8c922087fcdd21d1941961bc82cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113380"
---
# <a name="nmake-fatal-error-u1099"></a>Závažná chyba nástroje NMAKE U1099

přetečení zásobníku

Zpracování souboru pravidel byla příliš složitý pro aktuální přidělení zásobníku v nástroji NMAKE. NMAKE má přidělený objem 0x3000 (12 kb / s).

Pro zvýšení přidělení zásobníku v NMAKE, spusťte [/Stack editbin](../../build/reference/stack.md) nástroj s větší možností zásobníku:

**Editbin – /STACK:reserve NMAKE. SOUBOR EXE**

kde *rezervovat* je větší než aktuální přidělení zásobníku v nástroji NMAKE číslo.