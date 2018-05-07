---
title: CDynamicAccessor::SetStatus | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicAccessor::SetStatus
- ATL::CDynamicAccessor::SetStatus
- CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetStatus
dev_langs:
- C++
helpviewer_keywords:
- SetStatus method
ms.assetid: 6db82694-e87d-4bf8-a7e3-5765cf6abff9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7bf0fd390699d83261cf52651a3dc16613fa70d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessorsetstatus"></a>CDynamicAccessor::SetStatus
Nastaví stav pro určený sloupec.  
  
## <a name="syntax"></a>Syntaxe  
  
```
bool SetStatus(DBORDINAL nColumn,   
   DBSTATUS status)throw();  

bool SetStatus(const CHAR* pColumnName,   
   DBSTATUS status) throw();  

bool SetStatus(const WCHAR* pColumnName,   
   DBSTATUS status) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nColumn`  
 [v] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.  
  
 *Stav*  
 [v] Sloupec Stav. V tématu [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) v *referenční příručka programátora technologie OLE DB* Další informace.  
  
 `pColumnName`  
 [v] Ukazatel na řetězec znaků, který obsahuje název sloupce.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je zadaný sloupec Stav úspěšně. Jinak, funkce vrátí hodnotu **false**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::GetStatus](../../data/oledb/cdynamicaccessor-getstatus.md)