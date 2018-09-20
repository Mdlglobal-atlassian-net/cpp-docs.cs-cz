---
title: skryté | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.hidden
dev_langs:
- C++
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 726a44a33be5fe82986d4696c5420e07d5c103ff
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416458"
---
# <a name="hidden"></a>hidden

Označuje, že položka existuje, ale nebude se zobrazovat v prohlížeči uživatele.

## <a name="syntax"></a>Syntaxe

```cpp
[hidden]
```

## <a name="remarks"></a>Poznámky

**Skryté** C++ atribut má stejné funkce jako [skryté](/windows/desktop/Midl/hidden) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [umožňujících vazbu](../windows/bindable.md) příklad, jak používat **skryté**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**rozhraní**, **třídy**, **struktura**, metoda, vlastnost|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|**coclass** (při použití u **třídy** nebo **struktura**)|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)<br/>
[Atributy rozhraní](../windows/interface-attributes.md)<br/>
[Atributy třídy](../windows/class-attributes.md)<br/>
[Atributy metody](../windows/method-attributes.md)  