---
title: "CDynamicParameterAccessor – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicParameterAccessor class
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6c0bf234bd0f8a3de96c545e2bbdfe492822d627
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor – třída
Podobně jako [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) ale získává informace o parametrech, chcete-li nastavit, že zavoláte [ICommandWithParameters](https://msdn.microsoft.com/en-us/library/ms712937.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-cdynamicparameteraccessor.md)|Konstruktor|  
|[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)|Načte parametr dat z vyrovnávací paměti.|  
|[GetParamCount](../../data/oledb/cdynamicparameteraccessor-getparamcount.md)|Načte počet parametrů v přistupujícím objektu.|  
|[GetParamIO](../../data/oledb/cdynamicparameteraccessor-getparamio.md)|Určuje, zda je zadaný parametr vstupní nebo výstupní parametr.|  
|[GetParamLength](../../data/oledb/cdynamicparameteraccessor-getparamlength.md)|Načte délka zadaný parametr uložené ve vyrovnávací paměti.|  
|[GetParamName](../../data/oledb/cdynamicparameteraccessor-getparamname.md)|Načte název zadaného parametru.|  
|[GetParamStatus](../../data/oledb/cdynamicparameteraccessor-getparamstatus.md)|Načte stav zadaný parametr uložené ve vyrovnávací paměti.|  
|[GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md)|Načte řetězec data zadaný parametr uložené ve vyrovnávací paměti.|  
|[GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)|Načte datový typ zadaný parametr.|  
|[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)|Nastaví vyrovnávací paměti, pomocí parametru data.|  
|[SetParamLength](../../data/oledb/cdynamicparameteraccessor-setparamlength.md)|Nastaví délku zadaný parametr uložené ve vyrovnávací paměti.|  
|[SetParamStatus](../../data/oledb/cdynamicparameteraccessor-setparamstatus.md)|Nastaví stav zadaný parametr uložené ve vyrovnávací paměti.|  
|[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)|Nastaví data řetězce zadaného parametru uložené ve vyrovnávací paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Zprostředkovatel musí podporovat `ICommandWithParameters` pro příjemce k použití této třídy.  
  
 Informace o parametru je uložen do vyrovnávací paměti, vytvořit a spravovat touto třídou. Parametr data získáte z vyrovnávací paměti pomocí [GetParam –](../../data/oledb/cdynamicparameteraccessor-getparam.md) a [GetParamType –](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).  
  
 Příklad, který ukazuje, jak používat tuto třídu pro spuštění systému SQL Server uložené procedury a získat hodnoty parametrů výstup, článku znalostní báze Q058860, "postupy: provedení uložené procedury pomocí CDynamicParameterAccessor." Články znalostní báze jsou k dispozici v dokumentaci sady Visual Studio knihovny MSDN nebo v [http://support.microsoft.com/](http://support.microsoft.com).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví**: také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor – třída](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)   
 [CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)