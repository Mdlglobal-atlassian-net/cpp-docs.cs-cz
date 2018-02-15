---
title: CCommand::Create | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CCommand.Create
- CCommand::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method [C++]
ms.assetid: e4bede7a-68bd-491a-97f4-89b03d45cd24
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e84809d24479d85b01441c67b467102936b7f1aa
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ccommandcreate"></a>CCommand::Create
Volání [CCommand::CreateCommand](../../data/oledb/ccommand-createcommand.md) vytvořit příkaz pro zadaná relace, pak zavolá [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) zadat text příkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CCommandBase::Create(const CSession& session,   
   LPCWSTR wszCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();  


HRESULT CCommandBase::Create(const CSession& session,   
   LPCSTR szCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 `session`  
 [v] Relace, na kterém chcete vytvořit příkaz.  
  
 `wszCommand`  
 [v] Ukazatel text v kódu Unicode příkazového řetězce.  
  
 `szCommand`  
 [v] Ukazatel na ANSI text příkazu řetězce.  
  
 `guidCommand`  
 [v] Identifikátor GUID, který určuje syntaxi a obecná pravidla pro zprostředkovatele, který má používat při analýze text příkazu. Popis dialekty najdete v tématu [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 První formu **vytvořit** trvá příkazového řetězce Unicode. O druhou podobu **vytvořit** přebírá řetězec příkaz ANSI (poskytuje se kvůli zpětné kompatibilitě se stávajícími aplikacemi ANSI).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CCommand – třída](../../data/oledb/ccommand-class.md)