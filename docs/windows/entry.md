---
title: Položka | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.entry
dev_langs:
- C++
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: db90390be5313ddbea1103105f47b55fe9e23d62
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872312"
---
# <a name="entry"></a>entry
V modulu určením vstupní bod v knihovně DLL Určuje exportované funkce nebo konstanta.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ entry(  
   id  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 ID vstupního bodu.  
  
## <a name="remarks"></a>Poznámky  
 **Položka** atribut C++ má stejné funkce jako [položka](http://msdn.microsoft.com/library/windows/desktop/aa366815) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [idl_module –](../windows/idl-module.md) pro příklad použití **položka**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`idl_module` Atribut|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
