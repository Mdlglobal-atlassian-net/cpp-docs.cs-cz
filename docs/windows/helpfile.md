---
title: HelpFile – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpfile
dev_langs:
- C++
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3c2714c1418c5c9828322561ae1d7ca86dc6130a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647733"
---
# <a name="helpfile"></a>helpfile
Nastaví název souboru nápovědy pro knihovnu typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ helpfile(  
   "filename"  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Název souboru*  
 Název souboru, který obsahuje témata nápovědy.  
  
## <a name="remarks"></a>Poznámky  
 **HelpFile –** C++ atribut má stejné funkce jako [HelpFile –](http://msdn.microsoft.com/library/windows/desktop/aa366853) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [modulu](../windows/module-cpp.md) příklad, jak používat **HelpFile –**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**rozhraní**, **typedef**, **třídy**, metoda, **vlastnost**|  
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
 [HelpContext](../windows/helpcontext.md)   
 [helpstring](../windows/helpstring.md)   