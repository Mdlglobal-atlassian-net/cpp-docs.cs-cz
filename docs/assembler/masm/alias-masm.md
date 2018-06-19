---
title: ALIAS (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 7b14e1c41a448d0cb7014dabc50a42305249938f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049164"
---
# <a name="alias-masm"></a>ALIAS (MASM)
**ALIAS** – direktiva vytvoří alternativní název pro funkci.  To umožňuje vytvořit více názvů pro funkci nebo knihovny, které umožňují linkeru (LINK.exe) pro mapování staré funkce na novou funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALIAS  <  
alias  
> = <  
actual-name  
>  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `actual-name`  
 Skutečný název funkce nebo procedury.  Lomené závorky jsou povinné.  
  
 `alias`  
 Název alternativní nebo alias.  Lomené závorky jsou povinné.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)