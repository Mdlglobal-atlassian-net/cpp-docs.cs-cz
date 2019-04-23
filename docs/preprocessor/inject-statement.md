---
title: inject_statement
ms.date: 10/18/2018
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: 237ca796028aad7aff55442eb2806fe400330a29
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034284"
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

## <a name="see-also"></a>Viz také:

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)