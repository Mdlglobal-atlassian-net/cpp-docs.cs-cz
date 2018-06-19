---
title: auto_inline – | Microsoft Docs
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
ms.openlocfilehash: de012a31fe68c68d4e64df2d3fa10b44d9112735
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33954018"
---
# <a name="autoinline"></a>auto_inline
Vyloučí všechny funkcí definovaných v rozsahu, kde **vypnout** je zadán z se nepovažují za kandidáty pro automatické vložené rozšíření.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma auto_inline( [{on | off}] )  
```  
  
## <a name="remarks"></a>Poznámky  
 Použít **auto_inline –** – Direktiva pragma, umístěte ho před a okamžitě po (ne ve) definici funkce. Direktiva pragma se projeví u první definice funkce poté, co je direktiva pragma zobrazena.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)