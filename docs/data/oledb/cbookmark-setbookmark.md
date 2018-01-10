---
title: CBookmark::SetBookmark | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBookmark<0>::SetBookmark
- ATL.CBookmark<0>.SetBookmark
- CBookmark<0>.SetBookmark
- SetBookmark
- ATL::CBookmark::SetBookmark
- ATL::CBookmark<0>::SetBookmark
- CBookmark.SetBookmark
- ATL.CBookmark.SetBookmark
- CBookmark::SetBookmark
dev_langs: C++
helpviewer_keywords: SetBookmark method
ms.assetid: bcd26831-6045-4e69-96d6-abf8037fc18d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d30e21724bb7ee0d9d2bf7a6a5a094390fff645a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cbookmarksetbookmark"></a>CBookmark::SetBookmark
Zkopíruje hodnoty záložku odkazuje `pBuffer` k `CBookmark` vyrovnávací paměti a nastaví velikost vyrovnávací paměti na `nSize`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT SetBookmark(  
   DBLENGTH nSize,  
   BYTE* pBuffer   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *nSize*  
 [v] Velikost vyrovnávací paměti záložky.  
  
 `pBuffer`  
 [v] Ukazatel na bajtové pole obsahující hodnota záložky.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je k dispozici v pouze **CBookmark\<0 >**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CBookmark – třída](../../data/oledb/cbookmark-class.md)