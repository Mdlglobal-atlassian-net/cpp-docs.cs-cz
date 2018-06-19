---
title: CDataSource::GetInitializationString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
dev_langs:
- C++
helpviewer_keywords:
- GetInitializationString method
ms.assetid: 97134723-6e99-4004-a56d-ec57543dbf3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c2cc4652dcb7450217fd99969089bdbeb41c3a3f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094049"
---
# <a name="cdatasourcegetinitializationstring"></a>CDataSource::GetInitializationString
Načte inicializačního řetězce zdroje dat, který je aktuálně otevřený.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetInitializationString(BSTR* pInitializationString,   
   bool bIncludePassword = false) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *pInitializationString*  
 [out] Ukazatel na inicializačního řetězce.  
  
 *bIncludePassword*  
 [v] **true** Pokud řetězec obsahuje heslo; v opačném případě **false**.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Výsledný řetězec inicializace lze později znovu otevřete tento připojení ke zdroji dat.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDataSource – třída](../../data/oledb/cdatasource-class.md)