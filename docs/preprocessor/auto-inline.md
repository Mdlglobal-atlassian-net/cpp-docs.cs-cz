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
ms.openlocfilehash: cc2fb4cb870ff1dca2f0b55e9aad20741ffb8220
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083175"
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