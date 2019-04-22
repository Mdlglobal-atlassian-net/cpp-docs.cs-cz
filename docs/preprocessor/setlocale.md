---
title: setlocale
ms.date: 11/04/2016
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
ms.openlocfilehash: b2f28a14b4d4585575a39dd9a936a56a84eeddc4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59022422"
---
# <a name="setlocale"></a>setlocale

Určuje národní prostředí (země/oblast a jazyk) při překladu konstant širokého znaku a řetězcových literálů.

## <a name="syntax"></a>Syntaxe

```
#pragma setlocale( "[locale-string]" )
```

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že se algoritmus převodu vícebajtových znaků na široké znaky může lišit na základě národního prostředí nebo mohou kompilace probíhat v jiném národní prostředí lišícího se od prostředí, kde bude spuštěn spustitelný soubor, poskytuje tato direktiva pragma způsob určení cílového národního prostředí v době kompilace. Tím je zaručeno, že řetězce širokého znaku budou uloženy ve správném formátu.

Výchozí hodnota *řetězec národního prostředí* je "".

Národní prostředí "C" mapuje každý znak v řetězci na jeho hodnotu jako **wchar_t** (unsigned short). Jiné hodnoty, které jsou platné pro `setlocale` jsou ty položky, které jsou součástí [Language Strings](../c-runtime-library/language-strings.md) seznamu. Je například možné setkat se s:

```cpp
#pragma setlocale("dutch")
```

Schopnost vydávat řetězec jazyka závisí na znakové stránce a podpoře ID jazyka na počítači.

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)