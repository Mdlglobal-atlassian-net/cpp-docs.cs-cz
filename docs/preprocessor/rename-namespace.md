---
title: rename_namespace
ms.date: 10/18/2018
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: 7b3917a7114ca44d092f10a7831bb35bc64e9387
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039870"
---
# <a name="renamenamespace"></a>rename_namespace

**Specifické pro C++**

Přejmenuje obor názvů, který obsahuje obsah knihovny typů.

## <a name="syntax"></a>Syntaxe

```
rename_namespace("NewName")
```

### <a name="parameters"></a>Parametry

*NewName*<br/>
Nový název oboru názvů.

## <a name="remarks"></a>Poznámky

Přijímá jeden argument, *NewName*, která určuje nový název pro obor názvů.

Chcete-li odebrat obor názvů, použijte [no_namespace](../preprocessor/no-namespace.md) místo atributu.

**Specifické pro END C++**

## <a name="see-also"></a>Viz také:

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)