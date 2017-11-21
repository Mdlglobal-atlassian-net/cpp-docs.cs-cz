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
ms.openlocfilehash: cf3cfd6d1b0e484b31769184b2fae5a6b012a58e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
