---
title: "soubor nápovědy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.helpfile
dev_langs: C++
helpviewer_keywords: helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 63987b4e1427f12925b55fa3570d80b9e3a4686d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
