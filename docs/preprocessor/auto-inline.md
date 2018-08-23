---
title: auto_inline | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
dev_langs:
- C++
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc1b8a3b8539fb4871e4a28f4635c8012b9f80a2
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466194"
---
# <a name="autoinline"></a>auto_inline
Nezahrnuje žádné funkce definované v rámci oblasti kde **vypnout** určen jako uvažovaný kandidát pro rozšíření automatického vložení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma auto_inline( [{on | off}] )  
```  
  
## <a name="remarks"></a>Poznámky  

Použít **auto_inline** – Direktiva pragma, třeba ji umístit ihned po (nikoli do ní) definice funkce. Direktiva pragma se projeví u první definice funkce poté, co je direktiva pragma zobrazena.  
  
## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)