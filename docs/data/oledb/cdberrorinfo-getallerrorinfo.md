---
title: CDBErrorInfo::GetAllErrorInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- GetAllErrorInfo method
ms.assetid: 630049fa-d296-497a-bbf6-f5d3d71d271d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2642694c8031980bc548839c760081bef570191a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="cdberrorinfogetallerrorinfo"></a>CDBErrorInfo::GetAllErrorInfo
Vrátí všechny typy informace o chybě obsažené v záznam chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```
HRESULT GetAllErrorInfo(ULONG ulRecordNum,  
   LCID lcid,  BSTR* pbstrDescription,  
   BSTR* pbstrSource = NULL,  
   GUID* pguid = NULL,  
   DWORD* pdwHelpContext = NULL,  
   BSTR* pbstrHelpFile = NULL) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *ulRecordNum*  
 [v] Číslo od nuly záznamu, který vrátí informace o chybě.  
  
 `lcid`  
 [v] ID národního prostředí má být vrácen, informace o chybě.  
  
 `pbstrDescription`  
 [out] Ukazatel na textový popis chyby nebo hodnota NULL, pokud národního prostředí není podporován. V části poznámky.  
  
 `pbstrSource`  
 [out] Ukazatel na řetězec, který obsahuje název komponenty, který vytvořil chybu.  
  
 `pguid`  
 [out] Ukazatel na identifikátor GUID rozhraní definované chyba.  
  
 *pdwHelpContext*  
 [out] Ukazatel na ID kontextu nápovědy k chybě.  
  
 *pbstrHelpFile*  
 [out] Ukazatel na řetězec obsahující cestu k souboru nápovědy, která popisuje danou chybu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud bylo úspěšné. V tématu [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) v *referenční příručka programátora technologie OLE DB* pro ostatní vrácené hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="remarks"></a>Poznámky  
 Hodnota výstupu `pbstrDescription` je interně získala při volání IErrorInfo::GetDescription, který nastaví hodnotu na hodnotu NULL, pokud nepodporuje národní prostředí, nebo pokud jsou splněny obě následující podmínky:  
  
1.  Hodnota `lcid` není USA Angličtina a  
  
2.  Hodnota `lcid` se nerovná hodnotě vrácené GetUserDefaultLCID.  
  
## <a name="see-also"></a>Viz také  
 [CDBErrorInfo – třída](../../data/oledb/cdberrorinfo-class.md)