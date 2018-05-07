---
title: BEGIN_ACCESSOR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BEGIN_ACCESSOR
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
ms.assetid: 59d0ff3e-7cfd-4ce8-9a1c-d664c0892a52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0ffb1d506a198586a5a625664f21c29954aada40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="beginaccessor"></a>BEGIN_ACCESSOR
Označuje začátek položku přistupujícího objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BEGIN_ACCESSOR(num, bAuto)  
```  
  
#### <a name="parameters"></a>Parametry  
 *Poče*  
 [v] Číslo nula posun přistupujícího objektu v této mapě přistupujícího objektu.  
  
 *bAuto*  
 [v] Určuje, zda je tento přistupující objekt přistupující objekt automatické nebo ruční přistupující objekt. Pokud **true**, pokud je přistupující automaticky; **false**, je ruční přistupující. Přistupující objekt automaticky znamená, že je pro vás na operace přesunutí načíst data.  
  
## <a name="remarks"></a>Poznámky  
 V případě více přístupových objektů pro sadu řádků, je třeba zadat `BEGIN_ACCESSOR_MAP` a použít `BEGIN_ACCESSOR` makro pro každé jednotlivé přistupujícího objektu. `BEGIN_ACCESSOR` Makro byla dokončena s `END_ACCESSOR` makro. `BEGIN_ACCESSOR_MAP` Makro byla dokončena s `END_ACCESSOR_MAP` makro.  
  
## <a name="example"></a>Příklad  
 V tématu [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)