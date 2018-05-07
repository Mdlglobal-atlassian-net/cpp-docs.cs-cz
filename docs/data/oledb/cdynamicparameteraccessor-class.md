---
title: CDynamicParameterAccessor – třída | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicParameterAccessor class
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1b9478a5b2cc2190219ce2b297d1908683577c9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor – třída

Podobně jako [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) ale získává informace o parametrech, chcete-li nastavit, že zavoláte [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) rozhraní.

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
|[Setparamstatus –](../../data/oledb/cdynamicparameteraccessor-setparamstatus.md)|Nastaví stav zadaný parametr uložené ve vyrovnávací paměti.|
|[Setparamstring –](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)|Nastaví data řetězce zadaného parametru uložené ve vyrovnávací paměti.|

## <a name="remarks"></a>Poznámky

Zprostředkovatel musí podporovat `ICommandWithParameters` pro příjemce k použití této třídy.

Informace o parametru je uložen do vyrovnávací paměti, vytvořit a spravovat touto třídou. Parametr data získáte z vyrovnávací paměti pomocí [GetParam –](../../data/oledb/cdynamicparameteraccessor-getparam.md) a [GetParamType –](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Příklad, který ukazuje, jak používat tuto třídu pro spuštění systému SQL Server uložené procedury a získat hodnoty parametrů výstup, naleznete v části [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) ukázkový kód v [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) úložišti na Githubu.

## <a name="requirements"></a>Požadavky

**Záhlaví**: také atldbcli.h

## <a name="see-also"></a>Viz také

[Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)  
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)  
[CAccessor – třída](../../data/oledb/caccessor-class.md)  
[CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)  
[CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)  
