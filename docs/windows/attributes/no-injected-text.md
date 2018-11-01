---
title: no_injected_text – (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: af4bb4b07439c0a5dacfa0d4956db564d2dccefe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618114"
---
# <a name="noinjectedtext"></a>no_injected_text

Zabrání kompilátoru vkládání kódu v důsledku použití atributu.

## <a name="syntax"></a>Syntaxe

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>Parametry

*Datový typ Boolean*<br/>
(Volitelné) **true** žádný kód vložený, chcete-li **false** umožňující kódu vložit. **Hodnota TRUE** je výchozí nastavení.

## <a name="remarks"></a>Poznámky

Nejběžnější použití nástroje **no_injected_text –** atributů C++, je [/Fx](../../build/reference/fx-merge-injected-code.md) – možnost kompilátoru, která vloží **no_injected_text –** atributu do souboru .mrg.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Kdekoli|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy kompilátoru](compiler-attributes.md)