---
title: jedinečné (atribut COM jazyka C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.unique
helpviewer_keywords:
- unique attribute
ms.assetid: abd7ed14-5ae7-44a8-8333-0058e9c92b2f
ms.openlocfilehash: c5d7a2d60dc295a4390f777a9ff3718f41321ddd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038787"
---
# <a name="unique-c"></a>unique (C++)

Určuje jedinečný ukazatel.

## <a name="syntax"></a>Syntaxe

```cpp
[unique]
```

## <a name="remarks"></a>Poznámky

**Jedinečný** C++ atribut má stejné funkce jako [jedinečný](/windows/desktop/Midl/unique) atribut MIDL.

## <a name="example"></a>Příklad

Najdete v článku [ref](ref-cpp.md) příklad ukázkový používání **jedinečný**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Definice TypeDef**, **struktura**, **sjednocení**, rozhraní parametr, rozhraní – metoda|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)