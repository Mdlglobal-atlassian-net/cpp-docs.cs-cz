---
title: "IConvertTypeImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
dev_langs: C++
helpviewer_keywords: IConvertTypeImpl class
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 293d5d02b9515db7356eb839ced8dc1d006daafb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl – třída
Představuje implementaci objektu [IConvertType](https://msdn.microsoft.com/en-us/library/ms715926.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class T>  
class ATL_NO_VTABLE IConvertTypeImpl   
   : public IConvertType, public CConvertHelper  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IConvertTypeImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[Canconvert –](../../data/oledb/iconverttypeimpl-canconvert.md)|Poskytuje informace o dostupnosti převody typů v příkazu nebo pro sadu řádků.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je povinná na příkazy, sady řádků a sady řádků index. **IConvertTypeImpl** implementuje rozhraní delegováním k objektu převod poskytl OLE DB.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)