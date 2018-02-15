---
title: CUtlProps::IsValidValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
dev_langs:
- C++
helpviewer_keywords:
- IsValidValue method
ms.assetid: 1164556e-8d98-429c-a396-fc9a699e0e97
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7c806b7fdeae18f53d9f8fd5d012bf67ce8b1ef6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cutlpropsisvalidvalue"></a>CUtlProps::IsValidValue
Slouží k ověření hodnotu před nastavením vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,  
   DBPROP* pDBProp);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iCurSet`  
 Index v poli sada vlastností; nula, pokud je sada pouze jednu vlastnost.  
  
 `pDBProp`  
 ID vlastnosti a nová hodnota v [DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx) struktury.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`. Vrátí výchozí hodnota je `S_OK`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud máte jakékoli rutiny ověřování, které chcete spustit na hodnotu, která se chystáte použít k nastavení vlastnosti, by měly přepsat tuto funkci. Například může ověřit **DBPROP_AUTH_PASSWORD** s tabulkou heslo Určete platnou hodnotu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [CUtlProps – třída](../../data/oledb/cutlprops-class.md)