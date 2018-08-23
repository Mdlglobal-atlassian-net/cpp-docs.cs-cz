---
title: out (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.out
dev_langs:
- C++
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 220adeb44e676937756cf8007647f7e381f7607f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597557"
---
# <a name="out-c"></a>out (C++)

Identifikuje parametry ukazatele, které se vracejí z volané procedury do volající procedury (ze serveru do klienta).

## <a name="syntax"></a>Syntaxe

```cpp
[out]
```

## <a name="remarks"></a>Poznámky

**Si** C++ atribut má stejné funkce jako [si](http://msdn.microsoft.com/library/windows/desktop/aa367136) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [umožňujících vazbu](../windows/bindable.md) ukázkový používání **si**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Parametr rozhraní|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy parametru](../windows/parameter-attributes.md)  
[defaultvalue](../windows/defaultvalue.md)  
[id](../windows/id.md)  