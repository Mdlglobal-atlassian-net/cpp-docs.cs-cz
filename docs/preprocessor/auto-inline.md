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
ms.openlocfilehash: a3e49941271ec294ddb69861d12e3451332770fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633338"
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