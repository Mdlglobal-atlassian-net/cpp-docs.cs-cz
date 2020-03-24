---
title: no_injected_text (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 5f98be3478b2e1eeb4b464f1784f3f4ece22d8a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166611"
---
# <a name="no_injected_text"></a>no_injected_text

Zabraňuje kompilátoru v vkládání kódu v důsledku použití atributu.

## <a name="syntax"></a>Syntaxe

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>Parametry

*datového*<br/>
Volitelné **true** , pokud nechcete, aby byl kód vložen, **false** , aby bylo možné vložit kód. výchozí **hodnota je true** .

## <a name="remarks"></a>Poznámky

Nejběžnějším použitím atributu **No_injected_text** C++ je možnost kompilátoru [/FX](../../build/reference/fx-merge-injected-code.md) , která vloží atribut **No_injected_text** do souboru. mrg.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Jakékoli|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy kompilátoru](compiler-attributes.md)
