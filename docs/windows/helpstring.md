---
title: helpstring | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstring
dev_langs:
- C++
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 81a3e45c5636fd193b7880e093711b5cc584bf99
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879003"
---
# <a name="helpstring"></a>helpstring
Určuje řetězec znaků, který se používá k popisu elementu, na který se vztahuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ helpstring(  
   "string"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `string`  
 Textový řetězec nápovědy.  
  
## <a name="remarks"></a>Poznámky  
 **Helpstring** atribut C++ má stejné funkce jako [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [defaultvalue](../windows/defaultvalue.md) příklad použití **helpstring**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`interface`, `typedef`, **třída**, metoda, vlastnost|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Soubor nápovědy](../windows/helpfile.md)   
 [helpcontext](../windows/helpcontext.md)   
