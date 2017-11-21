---
title: ID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.id
dev_langs: C++
helpviewer_keywords: id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c9110bfe44ea1ffe373ab5e3ed5d4aa3e06c2574
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [na více systémů](../windows/out-cpp.md)   
