---
title: CUtlProps::IsValidValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
dev_langs: C++
helpviewer_keywords: IsValidValue method
ms.assetid: 1164556e-8d98-429c-a396-fc9a699e0e97
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 06193b8c560c5ac6006698813222e698a98bccc3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cutlpropsisvalidvalue"></a>CUtlProps::IsValidValue
Slouží k ověření hodnotu před nastavením vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      virtual HRESULT CUtlPropsBase::IsValidValue(  
   ULONG /* iCurSet */,  
   DBPROP* pDBProp   
);  
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