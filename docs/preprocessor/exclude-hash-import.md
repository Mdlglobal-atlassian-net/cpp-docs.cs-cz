---
title: vyloučit (#import) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- exclude
dev_langs:
- C++
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c345d9268f63a714eeae4beff78a7ac39ce545a1
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807897"
---
# <a name="exclude-import"></a>vyloučit (\#import)

**Specifické pro C++**

Vyloučí položky z generovaných souborů hlaviček knihoven typů.

## <a name="syntax"></a>Syntaxe

```
exclude("Name1"[, "Name2",...])
```

### <a name="parameters"></a>Parametry

*Name1*<br/>
První položka, která má být vyloučena.

*Name2*<br/>
Druhá položka, která má být vyloučena (je-li zapotřebí).

## <a name="remarks"></a>Poznámky

Knihovny typů mohou obsahovat definice položek definovaných v systémových hlavičkách nebo jiných knihovnách typů. Tento atribut může přijmout libovolný počet argumentů, přičemž každý z nich je položkou knihovny typů nejvyšší úrovně, která má být vyloučena.

**Specifické pro END C++**

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)