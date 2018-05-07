---
title: CRowsetImpl::ValidateCommandID | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
dev_langs:
- C++
helpviewer_keywords:
- ValidateCommandID method
ms.assetid: cdde6088-41bc-4b8f-a32b-f36f7d9b5ec0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6b83f0e8bb65a6043a9ca48f87ffe8babfb73e22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetimplvalidatecommandid"></a>CRowsetImpl::ValidateCommandID
Zkontroluje, zda buď nebo obojí **DBID**s obsahovat řetězcové hodnoty a pokud ano, kopíruje je do svých členů dat [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pTableID`  
 [v] Ukazatel **DBID** představující ID tabulky.  
  
 `pIndexID`  
 [v] Ukazatel **DBID** představující ID indexu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je volána prostřednictvím statických přetypování nahoru podle `CRowsetImpl` k naplnění jeho datové členy [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Ve výchozím nastavení, tato metoda zkontroluje, zda buď nebo obojí **DBID**s obsahovat řetězcové hodnoty a pokud ano, kopíruje je do svých dat členů. Tím, že metoda s Tento podpis ve vaší `CRowsetImpl`-odvozené třídy, nezavolá se vaše metoda místo základní implementaci.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [CRowsetImpl – třída](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)