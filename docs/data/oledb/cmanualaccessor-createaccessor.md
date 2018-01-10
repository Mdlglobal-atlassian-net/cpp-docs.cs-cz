---
title: CManualAccessor::CreateAccessor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
dev_langs: C++
helpviewer_keywords: CreateAccessor method
ms.assetid: 594c8d6d-b49a-4818-a9a5-81c8115d4e42
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f313e6d2b13a03a91295c75d52e4e77d5dfda22b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmanualaccessorcreateaccessor"></a>CManualAccessor::CreateAccessor
Přidělí paměť pro sloupec struktury vazby a inicializuje data členy sloupců.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT CreateAccessor(   
   int nBindEntries,   
   void* pBuffer,   
   DBLENGTH nBufferSize    
) throw( );  
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