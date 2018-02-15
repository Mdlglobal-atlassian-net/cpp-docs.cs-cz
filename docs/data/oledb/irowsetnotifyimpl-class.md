---
title: "IRowsetNotifyImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyImpl class
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8e23103cf4505ffb2bc683c69d22628fa15b861d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl – třída
Implementuje a zaregistruje [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) na příjemce (také označované jako "jímka"), aby ho mohl zpracovávat oznámení.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[OnFieldChange](../../data/oledb/irowsetnotifyimpl-onfieldchange.md)|Upozorní příjemce všechny změny na hodnotu sloupce.|  
|[OnRowChange](../../data/oledb/irowsetnotifyimpl-onrowchange.md)|Upozorní spotřebitele první změna na řádek nebo všechny změny, která má vliv na celý řádek.|  
|[OnRowsetChange](../../data/oledb/irowsetnotifyimpl-onrowsetchange.md)|Upozorní příjemce všechny změny ovlivňující celou sadu řádků.|  
  
## <a name="remarks"></a>Poznámky  
 V tématu [příjem oznámení](../../data/oledb/receiving-notifications.md) o implementaci rozhraní bodu připojení pro příjemce.  
  
 `IRowsetNotifyImpl` poskytuje implementaci pro fiktivní `IRowsetNotify`, s prázdnou funkce pro `IRowsetNotify` metody [onfieldchange –](https://msdn.microsoft.com/en-us/library/ms715961.aspx), [onrowchange –](https://msdn.microsoft.com/en-us/library/ms722694.aspx), a [onrowsetchange –](https://msdn.microsoft.com/en-us/library/ms722669.aspx). Pokud jste z této třídy dědit při implementaci `IRowsetNotify` rozhraní, můžete implementovat jenom metody, které potřebujete. Potřebujete poskytovat prázdný implementace pro jiné metody sami.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)   
 [IRowsetNotifyCP – třída](../../data/oledb/irowsetnotifycp-class.md)