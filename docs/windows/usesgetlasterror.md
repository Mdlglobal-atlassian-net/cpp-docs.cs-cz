---
title: usesgetlasterror – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.usesgetlasterror
dev_langs:
- C++
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 011cf954a0b111e46afcaf6e55a54914075864db
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014559"
---
# <a name="usesgetlasterror"></a>usesgetlasterror
Říká volajícímu, že pokud dojde k chybě při volání této funkce, potom volající provést zavoláním `GetLastError` načíst kód chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[usesgetlasterror]  
```  
  
## <a name="remarks"></a>Poznámky  
 **Usesgetlasterror –** C++ atribut má stejné funkce jako [usesgetlasterror –](http://msdn.microsoft.com/library/windows/desktop/aa367297) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Zobrazit [možnost idl_module](../windows/idl-module.md) příklad ukázku toho, jak používat **usesgetlasterror –**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**modul** atribut|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   