---
title: no_injected_text – (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.no_injected_text
dev_langs:
- C++
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3169c58d192b80400bada8c403f8a769cfb11f55
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069981"
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