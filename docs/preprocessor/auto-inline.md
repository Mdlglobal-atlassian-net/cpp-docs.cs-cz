---
title: auto_inline
ms.date: 11/04/2016
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
ms.openlocfilehash: c59dcc8ec7749a91565d5af043b1bd9e9eaa16ea
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033161"
---
# <a name="autoinline"></a>auto_inline
Nezahrnuje žádné funkce definované v rámci oblasti kde **vypnout** určen jako uvažovaný kandidát pro rozšíření automatického vložení.

## <a name="syntax"></a>Syntaxe

```
#pragma auto_inline( [{on | off}] )
```

## <a name="remarks"></a>Poznámky

Použít **auto_inline** – Direktiva pragma, třeba ji umístit ihned po (nikoli do ní) definice funkce. Direktiva pragma se projeví u první definice funkce poté, co je direktiva pragma zobrazena.

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)