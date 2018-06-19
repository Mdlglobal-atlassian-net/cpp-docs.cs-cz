---
title: soubor nápovědy | Microsoft Docs
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
ms.openlocfilehash: 926d0fec27bf323f559ad2fe0dffbd4208b1bf2a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876186"
---
# <a name="helpfile"></a>helpfile
Nastaví název souboru nápovědy knihovny typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ helpfile(  
   "filename"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *Název souboru*  
 Název souboru, který obsahuje témata nápovědy.  
  
## <a name="remarks"></a>Poznámky  
 **Soubor nápovědy** atribut C++ má stejné funkce jako [soubor nápovědy](http://msdn.microsoft.com/library/windows/desktop/aa366853) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [modulu](../windows/module-cpp.md) příklad použití **soubor nápovědy**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`interface`, `typedef`, **třída**, metoda, vlastnost|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [HelpContext –](../windows/helpcontext.md)   
 [helpstring](../windows/helpstring.md)   
