---
title: CCommand::Create | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CCommand.Create
- CCommand::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method [C++]
ms.assetid: e4bede7a-68bd-491a-97f4-89b03d45cd24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f85cfd9ed9938d76c28449fae01a87d3bb81a293
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095245"
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