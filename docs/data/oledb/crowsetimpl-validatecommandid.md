---
title: CRowsetImpl::ValidateCommandID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
dev_langs: C++
helpviewer_keywords: ValidateCommandID method
ms.assetid: cdde6088-41bc-4b8f-a32b-f36f7d9b5ec0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1e59ca9d64ea71edcf52d151a592848434a109f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetimplvalidatecommandid"></a>CRowsetImpl::ValidateCommandID
Zkontroluje, zda buď nebo obojí **DBID**s obsahovat řetězcové hodnoty a pokud ano, kopíruje je do svých členů dat [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT CRowsetBaseImpl::ValidateCommandID(  
   DBID* pTableID,  
   DBID* pIndexID   
);  
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