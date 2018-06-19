---
title: CDBErrorInfo::GetAllErrorInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 590215ddc5c62e5c717aebe196bc33ce7d514e7a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091904"
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