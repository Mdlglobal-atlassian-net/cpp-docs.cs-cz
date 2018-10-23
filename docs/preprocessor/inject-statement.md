---
title: inject_statement – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inject_statement
dev_langs:
- C++
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27b35c10e9e1953dc45dee1caf61d2e58c38d02d
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808640"
---
# <a name="injectstatement"></a>inject_statement

**Specifické pro C++**

Vloží svůj argument jako zdrojový text do hlavičky knihovny typů.

## <a name="syntax"></a>Syntaxe

```
inject_statement("source_text")
```

### <a name="parameters"></a>Parametry

*source_text*<br/>
Zdrojový text, který má být vložen do souboru hlaviček knihovny typů.

## <a name="remarks"></a>Poznámky

Text je umístěn na začátek deklarace oboru názvů, který zaobaluje obsah knihovny typů v souboru hlaviček.

**Specifické pro END C++**

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)