---
title: CDynamicStringAccessor::GetString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
dev_langs:
- C++
helpviewer_keywords:
- GetString method
ms.assetid: 4af27f27-7589-49f5-93d8-6ef05c023c8a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cc23fe73eb0d804d0b53950885b1b83aba58ff91
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicstringaccessorgetstring"></a>CDynamicStringAccessor::GetString
Načte zadaný sloupec dat jako řetězec.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      BaseType* GetString(DBORDINAL nColumn) const throw();  

BaseType* GetString(const CHAR* pColumnName) const throw();  

BaseType* GetString(const WCHAR* pColumnName) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nColumn`  
 [v] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.  
  
 `pColumnName`  
 [v] Ukazatel na řetězec znaků, který obsahuje název sloupce.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na hodnotu řetězce načítají zadaný sloupec. Hodnota je typu ***BaseType***, která bude **CHAR** nebo **WCHAR** v závislosti na tom, jestli je definován _UNICODE nebo ne. Vrátí hodnotu NULL, pokud zadaný sloupec nebyl nalezen.  
  
## <a name="remarks"></a>Poznámky  
 Druhý přepsat trvá formuláře název sloupce jako řetězec ANSI. Třetí přepsat trvá formuláře název sloupce jako řetězec znaků Unicode.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicStringAccessor – třída](../../data/oledb/cdynamicstringaccessor-class.md)