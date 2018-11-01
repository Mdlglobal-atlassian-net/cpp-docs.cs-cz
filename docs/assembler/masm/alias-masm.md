---
title: ALIAS (MASM)
ms.date: 08/30/2018
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: ab00092f410d34119e876db4562e6d0709743d79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483496"
---
# <a name="alias-masm"></a>ALIAS (MASM)

**ALIAS** direktiva vytvoří alternativní název funkce.  To umožňuje vytvářet více názvů pro funkce, nebo knihovny, které umožňují linker (LINK.exe) pro mapování staré funkce na novou funkci.

## <a name="syntax"></a>Syntaxe

> ALIAS \< *alias*> = \< *skutečný název*>

#### <a name="parameters"></a>Parametry

*skutečný název*<br/>
Skutečný název funkce nebo procedury.  Lomené závorky jsou povinné.

*Alias*<br/>
Název alternativu nebo alias.  Lomené závorky jsou povinné.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>