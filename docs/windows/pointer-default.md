---
title: pointer_default – | Microsoft Docs
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
ms.openlocfilehash: ee904f9243cf642d3a942d4bc323f5ec381b0480
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="pointerdefault"></a>pointer_default
Určuje výchozí atribut ukazatele pro všechny ukazatele, s výjimkou ukazatele nejvyšší úrovně, které se zobrazují v seznamy parametrů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ pointer_default(  
   value  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *value*  
 Hodnota, která popisuje je ukazatel typu: **ptr**, `ref`, nebo **jedinečný**.  
  
## <a name="remarks"></a>Poznámky  
 **Pointer_default –** atribut C++ má stejné funkce jako [pointer_default –](http://msdn.microsoft.com/library/windows/desktop/aa367141) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [defaultvalue](../windows/defaultvalue.md) pro ukázkové použití **pointer_default –**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`interface`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
