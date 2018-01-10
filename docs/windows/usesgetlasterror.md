---
title: "usesgetlasterror – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.usesgetlasterror
dev_langs: C++
helpviewer_keywords: usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05c74f1254230270654b3dc0b44f541e4fe9ef2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="usesgetlasterror"></a>usesgetlasterror
Informuje volající, že pokud dojde k chybě při volání této funkce, volající může potom zavolejte `GetLastError` načíst kód chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[usesgetlasterror]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 **Usesgetlasterror –** atribut C++ má stejné funkce jako [usesgetlasterror –](http://msdn.microsoft.com/library/windows/desktop/aa367297) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Najdete v článku [idl_module –](../windows/idl-module.md) příklad ukázka, jak pomocí **usesgetlasterror –**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**modul** atribut|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
