---
title: "IRowsetInfoImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
dev_langs: C++
helpviewer_keywords: IRowsetInfoImpl class
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cba03cfdda0b7a55c8f4719d5340566ee5dc6050
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl – třída
Poskytuje implementaci pro [IRowsetInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE IRowsetInfoImpl :   
   public IRowsetInfo,    
   public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IRowsetInfoImpl`.  
  
 `PropClass`  
 Uživatelská vlastnost třídu, která použije se výchozí hodnota `T`.  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[GetProperties –](../../data/oledb/irowsetinfoimpl-getproperties.md)|Vrátí aktuální nastavení všech vlastností nepodporuje sadu řádků.|  
|[Getreferencedrowset –](../../data/oledb/irowsetinfoimpl-getreferencedrowset.md)|Vrátí sadu řádků, na které se vztahuje záložku ukazatele rozhraní.|  
|[Getspecification –](../../data/oledb/irowsetinfoimpl-getspecification.md)|Vrátí ukazatele rozhraní v objektu (příkaz nebo relace), který vytvořen této sady řádků.|  
  
## <a name="remarks"></a>Poznámky  
 Povinné rozhraní sady řádků. Tato třída implementuje pomocí vlastnosti sady řádků [mapy sady vlastností](../../data/oledb/begin-propset-map.md) definovaný ve třídě příkaz. I když třídy sady řádků se zobrazí, se pomocí příkazu třídy vlastnost nastaví, sady řádků se dodává s vlastní kopii vlastnostech spuštění při vytvoření objektu příkaz nebo relace.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** altdb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)