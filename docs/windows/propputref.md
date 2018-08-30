---
title: propputref | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propputref
dev_langs:
- C++
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b0b36342b7760eea074fe15506386bb3d7ce6764
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221239"
---
# <a name="propputref"></a>propputref

Určuje vlastnost nastavení funkci, která používá odkaz namísto hodnotu.

## <a name="syntax"></a>Syntaxe

```cpp
[propputref]
```

## <a name="remarks"></a>Poznámky

**Propputref** C++ atribut má stejné funkce jako [propputref](/windows/desktop/Midl/propputref) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [umožňujících vazbu](../windows/bindable.md) ukázkový používání **propputref**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Metoda|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|`propget`, `propput`|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy metody](../windows/method-attributes.md)  
[propget](../windows/propget.md)  
[propput](../windows/propput.md)  