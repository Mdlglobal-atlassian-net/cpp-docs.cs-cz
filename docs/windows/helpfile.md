---
title: HelpFile – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpfile
dev_langs:
- C++
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 66cd89c28ea01c3a75d0cb25aa6f96a234e379b2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418200"
---
# <a name="helpfile"></a>helpfile

Nastaví název souboru nápovědy pro knihovnu typů.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpfile(
   "filename"
) ]
```

### <a name="parameters"></a>Parametry

*Název souboru*<br/>
Název souboru, který obsahuje témata nápovědy.

## <a name="remarks"></a>Poznámky

**HelpFile –** C++ atribut má stejné funkce jako [HelpFile –](/windows/desktop/Midl/helpfile) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [modulu](../windows/module-cpp.md) příklad, jak používat **HelpFile –**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**rozhraní**, **typedef**, **třídy**, metoda, **vlastnost**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)<br/>
[Atributy rozhraní](../windows/interface-attributes.md)<br/>
[Atributy třídy](../windows/class-attributes.md)<br/>
[Atributy metody](../windows/method-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](../windows/helpcontext.md)<br/>
[helpstring](../windows/helpstring.md)  