---
title: IRowsetNotifyImpl – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyImpl class
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 860b735863acbcac869a4a297984084946aaf028
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106255"
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
|[Onfieldchange –](../../data/oledb/irowsetnotifyimpl-onfieldchange.md)|Upozorní příjemce všechny změny na hodnotu sloupce.|  
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