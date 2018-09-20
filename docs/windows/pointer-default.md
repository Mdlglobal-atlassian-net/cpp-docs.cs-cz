---
title: pointer_default – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pointer_default
dev_langs:
- C++
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 54b02ab188ddd122bd3751f73a3edb33d87266f9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388209"
---
# <a name="pointerdefault"></a>pointer_default

Určuje výchozí atribut ukazatele pro všechny odkazy, s výjimkou ukazatelů nejvyšší úrovně, které se zobrazí v seznamech parametrů.

## <a name="syntax"></a>Syntaxe

```cpp
[ pointer_default(
   value
) ]
```

### <a name="parameters"></a>Parametry

*value*<br/>
Hodnota, která popisuje typ ukazatele: **ptr**, **ref**, nebo **jedinečný**.

## <a name="remarks"></a>Poznámky

**Pointer_default –** C++ atribut má stejné funkce jako [pointer_default –](/windows/desktop/Midl/pointer-default) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [defaultvalue](../windows/defaultvalue.md) ukázkový používání **pointer_default –**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**interface**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)<br/>
[Atributy rozhraní](../windows/interface-attributes.md)  