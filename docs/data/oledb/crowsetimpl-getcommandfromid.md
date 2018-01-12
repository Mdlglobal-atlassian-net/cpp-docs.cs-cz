---
title: CRowsetImpl::GetCommandFromID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowsetImpl::GetCommandFromID
- GetCommandFromID
- CRowsetImpl.GetCommandFromID
dev_langs: C++
helpviewer_keywords: GetCommandFromID method
ms.assetid: 9f39cb07-1c40-486f-ba5b-cb4a65fab8a7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e75fbd00b6ee2e4a19cf0fe39d0bcda9f0314f8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetimplgetcommandfromid"></a>CRowsetImpl::GetCommandFromID
Kontroluje, zda nebo oba parametry obsahovat řetězcové hodnoty, a pokud ano, zkopíruje řetězcové hodnoty datových členů [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT CRowsetBaseImpl::GetCommandFromID(  
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
 Tato metoda je volána prostřednictvím statických přetypování nahoru podle `CRowsetImpl` k naplnění datových členů [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Ve výchozím nastavení zkontroluje tato metoda, pokud nebo oba parametry obsahovat řetězcové hodnoty. Pokud obsahují řetězcové hodnoty, tato metoda zkopíruje řetězcové hodnoty datových členů. Tím, že metoda s Tento podpis ve vaší `CRowsetImpl`-odvozené třídy, nezavolá se vaše metoda místo základní implementaci.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [CRowsetImpl – třída](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)