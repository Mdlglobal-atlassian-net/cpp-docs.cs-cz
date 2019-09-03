---
title: setlocale – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
ms.openlocfilehash: 219354595e5c63b2f13211d43bfa517d97413251
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218173"
---
# <a name="setlocale-pragma"></a>setlocale – direktiva pragma

Definuje *národní prostředí*, zemi, oblast a jazyk, které se mají použít při překladu konstant a řetězcových literálů s velkým znakem.

## <a name="syntax"></a>Syntaxe

> **#pragma setlocale ("** [ *locale-string* ] **")**

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že algoritmus pro převod vícebajtových znaků na široké znaky se může lišit podle národního prostředí, nebo může kompilace probíhat v jiném národním prostředí, ze kterého se spustí spustitelný soubor, tato direktiva pragma poskytuje způsob, jak určit cílové národní prostředí v době kompilace. Garantuje, že řetězce s velkým znakem jsou uloženy ve správném formátu.

Výchozí *národní prostředí-řetězec* je "".

Národní prostředí "C" mapuje každý znak v řetězci na jeho hodnotu jako **wchar_t**. Další platné hodnoty pro `setlocale` jsou záznamy, které se nacházejí v seznamu [řetězce jazyka](../c-runtime-library/language-strings.md) . Můžete například zadat:

```cpp
#pragma setlocale("dutch")
```

Možnost zadat řetězec jazyka závisí na znakové stránce a podpoře ID jazyka na vašem počítači.

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
