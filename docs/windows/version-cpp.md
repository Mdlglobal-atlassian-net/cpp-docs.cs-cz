---
title: verze (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 2c2d0c72ffbb805b526429562a5f39a09285b70f
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642276"
---
# <a name="version-c"></a>version (C++)
Určuje konkrétní verzi napříč několika verzemi třídu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ version(  
   "version"  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Verze*  
 Číslo verze `coclass`. Pokud není zadán, umístí 1.0 v souboru IDL.  
  
## <a name="remarks"></a>Poznámky  
 **Verze** C++ atribut má stejné funkce jako [verze](http://msdn.microsoft.com/library/windows/desktop/aa367306) atribut MIDL a předána do generovaného souboru.  
  
## <a name="example"></a>Příklad  
 Najdete v článku [umožňujících vazbu](../windows/bindable.md) příklad ukázkový používání **verze**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, **– struktura**|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|**coclass**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy kompilátoru](../windows/compiler-attributes.md)   
 [Atributy třídy](../windows/class-attributes.md)   