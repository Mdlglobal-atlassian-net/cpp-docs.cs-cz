---
title: ID | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.id
dev_langs:
- C++
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5a89758933aef4646aaf11d08d7193d48a44f468
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013542"
---
# <a name="id"></a>id
Určuje *dispid* parametr pro členské funkce (vlastnost nebo metoda v rozhraní nebo dispinterface).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ id(  
   dispid  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *identifikátor DISPID*  
 Identifikátor odeslání pro metody rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 **Id** C++ atribut má stejné funkce jako [id](http://msdn.microsoft.com/library/windows/desktop/aa367040) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [umožňujících vazbu](../windows/bindable.md) příklad, jak používat **id**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Metoda rozhraní|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [Atributy datového členu](../windows/data-member-attributes.md)   
 [Výchozí hodnota](../windows/defaultvalue.md)   
 [V](../windows/in-cpp.md)   
 [out](../windows/out-cpp.md)   