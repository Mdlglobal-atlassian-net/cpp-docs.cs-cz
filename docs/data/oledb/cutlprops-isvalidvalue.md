---
title: CUtlProps::IsValidValue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
dev_langs:
- C++
helpviewer_keywords:
- IsValidValue method
ms.assetid: 1164556e-8d98-429c-a396-fc9a699e0e97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0a37f0e0e9d415f9b7c78c8a619fd7fd66d24f28
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101962"
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