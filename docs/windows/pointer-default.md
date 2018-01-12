---
title: "pointer_default – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.pointer_default
dev_langs: C++
helpviewer_keywords: pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b55bf95c7abdffe8dd0a0e0071d86f06baad344e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
