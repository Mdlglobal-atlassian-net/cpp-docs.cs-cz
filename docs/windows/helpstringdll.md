---
title: helpstringdll – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringdll
dev_langs:
- C++
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2b1ba0c95a87ce1743d225fd6af4bffee148d6ab
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601890"
---
# <a name="helpstringdll"></a>helpstringdll

Určuje název knihovny DLL použít k provádění vyhledání řetězce dokumentu (lokalizace).

## <a name="syntax"></a>Syntaxe

```cpp
[ helpstringdll(
   "string"
) ]
```

### <a name="parameters"></a>Parametry

*string*  
Knihovny DLL použít k provádění vyhledání řetězce dokumentu.

## <a name="remarks"></a>Poznámky

**Helpstringdll –** C++ atribut má stejné funkce jako [helpstringdll –](http://msdn.microsoft.com/library/windows/desktop/aa366860) atribut MIDL.

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_helpstringdll.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib", helpstringdll="xx.dll")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI
{
   HRESULT xxx();
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **rozhraní**, rozhraní – metoda|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy rozhraní](../windows/interface-attributes.md)  
[Atributy třídy](../windows/class-attributes.md)  
[Atributy metody](../windows/method-attributes.md)  