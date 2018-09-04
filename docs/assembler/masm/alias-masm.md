---
title: ALIAS (MASM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Alias
dev_langs:
- C++
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6a977d35040d8ca25cd3bd4ae4def233092b37a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691059"
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