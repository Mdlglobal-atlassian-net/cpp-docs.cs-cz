---
title: "ICommandImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ICommandImpl
dev_langs: C++
helpviewer_keywords: ICommandImpl class
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c553effb6ad6a4aa9571eed62f30e4e83910afbd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="icommandimpl-class"></a>ICommandImpl – třída
Poskytuje implementaci pro [ICommand](https://msdn.microsoft.com/en-us/library/ms709737.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class T, class CommandBase = ICommand>   
class ATL_NO_VTABLE ICommandImpl : public CommandBase  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `ICommandImpl`.  
  
 `CommandBase`  
 Příkaz rozhraní. Výchozí hodnota je `ICommand`.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Cancelexecution –](../../data/oledb/icommandimpl-cancelexecution.md)|Zruší aktuální provedení příkazu.|  
|[Zrušit](../../data/oledb/icommandimpl-cancel.md)|Zruší aktuální provedení příkazu.|  
|[Createrowset –](../../data/oledb/icommandimpl-createrowset.md)|Vytvoří objekt sady řádků.|  
|[Spuštění](../../data/oledb/icommandimpl-execute.md)|Spustí příkaz.|  
|[Getdbsession –](../../data/oledb/icommandimpl-getdbsession.md)|Vrátí ukazatele rozhraní do relace, který vytvořili příkaz.|  
|[Icommandimpl –](../../data/oledb/icommandimpl-icommandimpl.md)|Konstruktor|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_bCancel](../../data/oledb/icommandimpl-m-bcancel.md)|Určuje, zda příkazu ke zrušení.|  
|[m_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)|Určuje, zda příkazu ke zrušení při provádění.|  
|[m_bIsExecuting](../../data/oledb/icommandimpl-m-bisexecuting.md)|Určuje, zda příkaz právě probíhá.|  
  
## <a name="remarks"></a>Poznámky  
 Povinné rozhraní pro objekt příkazu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)