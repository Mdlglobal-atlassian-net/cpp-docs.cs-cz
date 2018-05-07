---
title: CRowsetImpl::GetColumnInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetColumnInfo
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- GetColumnInfo method
ms.assetid: 9ef76525-f996-4c6f-81b9-68eb260350ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a989b31d672c9019d2ed5e61490f4e0042ab4c47
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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