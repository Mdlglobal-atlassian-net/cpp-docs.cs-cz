---
title: CManualAccessor::CreateAccessor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
dev_langs:
- C++
helpviewer_keywords:
- CreateAccessor method
ms.assetid: 594c8d6d-b49a-4818-a9a5-81c8115d4e42
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7d066bec37955d39ecee1fdca5522df843c84442
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cmanualaccessorcreateaccessor"></a>CManualAccessor::CreateAccessor
Přidělí paměť pro sloupec struktury vazby a inicializuje data členy sloupců.  
  
## <a name="syntax"></a>Syntaxe  
  
```
HRESULT CreateAccessor(int nBindEntries,   
  void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nBindEntries`  
 [v] Počet sloupců. Toto číslo se musí shodovat počet volání [CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) funkce.  
  
 `pBuffer`  
 [v] Ukazatel do vyrovnávací paměti uloží výstupní sloupce.  
  
 `nBufferSize`  
 [v] Velikost vyrovnávací paměti v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním volání této funkce `CManualAccessor::AddBindEntry` funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)   
 [Ukázka DBViewer](../../visual-cpp-samples.md)