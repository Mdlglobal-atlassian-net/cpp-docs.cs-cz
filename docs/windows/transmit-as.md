---
title: transmit_as – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.transmit_as
dev_langs:
- C++
helpviewer_keywords:
- transmit_as attribute
ms.assetid: 53d0b8ab-5b06-423e-83eb-3d01a10424b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5ec69b663b2a866701c2587d3913d23310aaf997
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013259"
---
# <a name="transmitas"></a>transmit_as
Instruuje kompilátor, aby přidružení uvedený typ, který manipulovat s klientské a serverové aplikace, přenášená typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ transmit_as(  
   type  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Typ*  
 Určuje typ dat, která se přenášejí mezi klientem a serverem.  
  
## <a name="remarks"></a>Poznámky  
 **Transmit_as –** C++ atribut má stejné funkce jako [transmit_as –](http://msdn.microsoft.com/library/windows/desktop/aa367286) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje použití **transmit_as –** atribut:  
  
```cpp  
// cpp_attr_ref_transmit_as.cpp  
// compile with: /LD  
#include "windows.h"  
[module(name="MyLibrary")];  
  
[export] typedef struct _TREE_NODE_TYPE {  
unsigned short data;   
struct _TREE_NODE_TYPE * left;  
struct _TREE_NODE_TYPE * right;   
} TREE_NODE_TYPE;  
  
[export] struct PACKED_NODE {  
   unsigned short data;   // same as normal node  
   int index;   // array index of parent  
};  
  
// A left node recursive built array of  
// the nodes in the tree.  Can be unpacked with  
// that knowledge  
[export] typedef struct _TREE_XMIT_TYPE {  
   int count;  
   [size_is(count)] PACKED_NODE node[];  
} TREE_XMIT_TYPE;  
  
[transmit_as(TREE_XMIT_TYPE)] typedef TREE_NODE_TYPE * TREE_TYPE;  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Definice TypeDef**|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [– TypeDef, Enum, Union a struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [export](../windows/export.md)   