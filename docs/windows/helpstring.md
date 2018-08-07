---
title: helpstring | Dokumentace Microsoftu
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
ms.openlocfilehash: e661e911cc0dd583f2ce079f8ac047a354fa596f
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570928"
---
# <a name="helpstring"></a>helpstring
Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ helpstring(  
   "string"  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *string*  
 Textový řetězec nápovědy.  
  
## <a name="remarks"></a>Poznámky  
 **Helpstring** C++ atribut má stejné funkce jako [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [defaultvalue](../windows/defaultvalue.md) příklad, jak používat **helpstring**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**rozhraní**, **typedef**, **třída**, metoda, vlastnost|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
 [Atributy třídy](../windows/class-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [– TypeDef, Enum, Union a struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Soubor nápovědy](../windows/helpfile.md)   
 [helpcontext](../windows/helpcontext.md)   