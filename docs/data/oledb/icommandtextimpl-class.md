---
title: ICommandTextImpl – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandText
dev_langs:
- C++
helpviewer_keywords:
- ICommandText class
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f49326dba4868ad490dc1a7122eed68271bdfa15
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100197"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl – třída
Poskytuje implementaci pro [ICommandText](https://msdn.microsoft.com/en-us/library/ms714914.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T >  
class ATL_NO_VTABLE ICommandTextImpl   
   : public ICommandImpl<T, ICommandText>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Příkaz třída odvozená z **ICommandTextImpl**.  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[Getcommandtext –](../../data/oledb/icommandtextimpl-getcommandtext.md)|Vrátí text příkazu nastavte posledním voláním do [SetCommandText –](../../data/oledb/icommandtextimpl-setcommandtext.md).|  
|[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)|Nastaví text příkazu, nahradí existující text příkazu.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_strCommandText](../../data/oledb/icommandtextimpl-m-strcommandtext.md)|Ukládá text příkazu.|  
  
## <a name="remarks"></a>Poznámky  
 Povinné rozhraní příkazy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** altdb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)