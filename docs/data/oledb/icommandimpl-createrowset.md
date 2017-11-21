---
title: ICommandImpl::CreateRowset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
dev_langs: C++
helpviewer_keywords: CreateRowset method
ms.assetid: a0890009-205e-4970-879f-01ed9d6a93f1
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 510f222972b8d9306f7b248799679f0dd499288a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="icommandimplcreaterowset"></a>ICommandImpl::CreateRowset
Voláno rozhraním [Execute](../../data/oledb/icommandimpl-execute.md) k vytvoření jedné sady řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      template <class   
      RowsetClass  
      >  
HRESULT CreateRowset(  
   IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `RowsetClass`  
 Člena třídy šablony představující uživatele třídy sady řádků. Obvykle je vygenerovat průvodcem.  
  
 `pUnkOuter`  
 [v] Ukazatel řízení **IUnknown** rozhraní Pokud sady řádků se vytváří v rámci agregace; jinak má hodnotu null.  
  
 `riid`  
 [v] Odpovídá `riid` v `ICommand::Execute`.  
  
 `pParams`  
 [vstup/výstup] Odpovídá `pParams` v `ICommand::Execute`.  
  
 `pcRowsAffected`  
 Odpovídá `pcRowsAffected` v `ICommand::Execute`.  
  
 `ppRowset`  
 [vstup/výstup] Odpovídá `ppRowset` v `ICommand::Execute`.  
  
 `pRowsetObj`  
 [out] Ukazatel na objektu sady řádků. Tento parametr se obvykle nepoužívá, ale můžete použít, pokud je třeba provést další práci na sadě řádků před předáním k objektu COM. Životnost `pRowsetObj` je svázaná s `ppRowset`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu. V tématu `ICommand::Execute` seznam typických hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Chcete vytvořit více než jedné sady řádků, nebo zadejte vlastní podmínky pro vytváření různé sady řádků, umístěte různých volání `CreateRowset` uvnitř **Execute**.  
  
 V tématu [ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) v *referenční příručka programátora prostředí OLE DB.*  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [ICommandImpl – třída](../../data/oledb/icommandimpl-class.md)