---
title: v aplikaci (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.in
dev_langs:
- C++
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cd6b79d84e4737cdbeb670bdd31b8cacf35cf8f1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373384"
---
# <a name="in-c"></a>in (C++)

Označuje, že je parametr předat z volající procedury do volané procedury.

## <a name="syntax"></a>Syntaxe

```cpp
[in]
```

## <a name="remarks"></a>Poznámky

**v** C++ atribut má stejné funkce jako [v](/windows/desktop/Midl/in) atribut MIDL.

## <a name="example"></a>Příklad

Zobrazit [umožňujících vazbu](../windows/bindable.md) příklad, jak používat **v**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Rozhraní parametrů, metody rozhraní|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|**retval**|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)<br/>
[Atributy parametru](../windows/parameter-attributes.md)<br/>
[Atributy metody](../windows/method-attributes.md)<br/>
[defaultvalue](../windows/defaultvalue.md)<br/>
[id](../windows/id.md)<br/>
[out](../windows/out-cpp.md)  