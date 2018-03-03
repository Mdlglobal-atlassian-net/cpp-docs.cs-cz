---
title: ID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.id
dev_langs:
- C++
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9225a87f32c3c7bf42ca5fc7de98dd0ab8f12639
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="id"></a>id
Určuje `dispid` parametr pro členské funkce (vlastnost nebo metodu, v rozhraní nebo dispinterface).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ id(  
   dispid  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `dispid`  
 Odesílání ID pro metodu rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 **Id** atribut C++ má stejné funkce jako [id](http://msdn.microsoft.com/library/windows/desktop/aa367040) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [vazbu](../windows/bindable.md) příklad použití **id**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Rozhraní – metoda|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [Atributy datového členu](../windows/data-member-attributes.md)   
 [Výchozí hodnota](../windows/defaultvalue.md)   
 [v](../windows/in-cpp.md)   
 [out](../windows/out-cpp.md)   
