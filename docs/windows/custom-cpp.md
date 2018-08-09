---
title: Vlastní (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.custom
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2c0f4f04adb9ddc847b1c22485d10512a9d684d0
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651892"
---
# <a name="custom-c"></a>custom (C++)
Definuje metadata pro objekt v knihovně typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ custom(  
   uuid,   
   value  
) ];  
```  
  
### <a name="parameters"></a>Parametry  
 *uuid*  
 Jedinečný identifikátor.  
  
 *value*  
 Hodnota, která můžou být přepnuté do hodnotu typu variant.  
  
## <a name="remarks"></a>Poznámky  
 **Vlastní** C++ atribut způsobí, že informace, které jde umístit do knihovny typů. Budete potřebovat nástroj, který čte vlastní hodnotu z knihovny typů.  
  
 **Vlastní** atribut má stejné funkce jako [vlastní](http://msdn.microsoft.com/library/windows/desktop/aa366766) atribut MIDL.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Non-COM **rozhraní**, **třídy**, **výčtu**s, `idl_module` metody, členy rozhraní, parametry rozhraní **typedef**s, **sjednocení**s, **struktura**s|  
|**Opakovatelné**|Ano|  
|**Vyžadované atributy**|**coclass** (při použití ve třídě)|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
 [– TypeDef, Enum, Union a struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [Atributy třídy](../windows/class-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   