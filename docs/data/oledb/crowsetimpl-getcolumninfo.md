---
title: CRowsetImpl::GetColumnInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetColumnInfo
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- GetColumnInfo method
ms.assetid: 9ef76525-f996-4c6f-81b9-68eb260350ef
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3cbcc7c25983680f32f1d5982188a853d8215358
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetimplgetcolumninfo"></a>CRowsetImpl::GetColumnInfo
Načte informace o sloupci pro požadavek na konkrétní klienta.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,  
   ULONG* pcCols);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pv`  
 [v] Ukazatel na uživatele `CRowsetImpl` odvozené třídy.  
  
 `pcCols`  
 [v] Ukazatel (výstup) počtu vrácených sloupců.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na statického **ATLCOLUMNINFO** struktura.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je pokročilé přepsání.  
  
 Tato metoda je volána několik základní implementaci třídy načíst informace o sloupci pro požadavek na konkrétní klienta. Obvykle, by se tato metoda volána `IColumnsInfoImpl`. Pokud tuto metodu přepíšete, musíte umístit verzi metody ve vaší `CRowsetImpl`-odvozené třídy. Protože metodu možné umístit ve třídě jiný-převést na šablonu, musíte změnit `pv` na příslušné `CRowsetImpl`-odvozené třídy.  
  
 Následující příklad ukazuje **na GetColumnInfo** využití. V tomto příkladu **CMyRowset** je `CRowsetImpl`-odvozené třídy. Chcete-li přepsat `GetColumnInfo` pro všechny instance této třídy, umístěte následující metodu v **CMyRowset** definici třídy:  
  
 [!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [CRowsetImpl – třída](../../data/oledb/crowsetimpl-class.md)