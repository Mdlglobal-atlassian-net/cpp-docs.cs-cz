---
title: verze (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.version
dev_langs:
- C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 43da63d75d3541915eba3e561ee08fe1048fa579
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890606"
---
# <a name="version-c"></a>version (C++)
Identifikuje na konkrétní verzi mezi více verzí třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ version(  
   "version"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *Verze*  
 Číslo verze coclass. Pokud není zadaný, 1.0 bude uložena v souboru IDL.  
  
## <a name="remarks"></a>Poznámky  
 **Verze** atribut C++ má stejné funkce jako [verze](http://msdn.microsoft.com/library/windows/desktop/aa367306) MIDL atribut a je předána do souboru generovaného IDL.  
  
## <a name="example"></a>Příklad  
 Najdete v článku [vazbu](../windows/bindable.md) příklad pro ukázkové použití **verze**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, `struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|**coclass**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy kompilátoru](../windows/compiler-attributes.md)   
 [Atributy třídy](../windows/class-attributes.md)   
