---
title: switch_is – (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_is
helpviewer_keywords:
- switch_is attribute
ms.assetid: f1fffe5d-12d2-4e0f-8803-ccb715177d2d
ms.openlocfilehash: ccac405480e415df17b42f02dce74759f578d025
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031086"
---
# <a name="switchis"></a>switch_is

Určuje výraz nebo identifikátor, který funguje jako sjednocení discriminant, který vybere člen sjednocení.

## <a name="syntax"></a>Syntaxe

```cpp
[switch_is]
```

## <a name="remarks"></a>Poznámky

**Switch_is –** C++ atribut má stejné funkce jako [switch_is –](/windows/desktop/Midl/switch-is) atribut MIDL.

## <a name="example"></a>Příklad

Najdete v článku [případ](case-cpp.md) příklad ukázkový používání **switch_is –**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**– definice typedef**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[switch_type](switch-type.md)