---
title: DEFINE_COMMAND_EX | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEFINE_COMMAND_EX
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND_EX macro
ms.assetid: d3e2ef20-1455-46d2-8499-8ab84bbb90a4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dae66cd7458eafd613c34fb03ac4b12f0962271f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="definecommandex"></a>DEFINE_COMMAND_EX
Určuje příkaz, který se použije k vytvoření dané sadě řádků při použití [CCommand](../../data/oledb/ccommand-class.md) třídy. Podporuje kódování Unicode a ANSI.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
DEFINE_COMMAND_EX(x, wszCommand)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *x*  
 [v] Název třída uživatelského záznamu (příkaz).  
  
 `wszCommand`  
 [v] Příkaz řetězec, který se použije k vytvoření dané sadě řádků při použití [CCommand](../../data/oledb/ccommand-class.md).  
  
## <a name="remarks"></a>Poznámky  
 Příkaz řetězec, který zadáte se použije jako výchozí, pokud nezadáte žádný text příkazu v [CCommand::Open](../../data/oledb/ccommand-open.md) metoda.  
  
 Toto makro přijme řetězců v kódu Unicode, bez ohledu na typ aplikace. Toto makro je upřednostňovaný přes [DEFINE_COMMAND](../../data/oledb/define-command.md) protože podporuje kódování Unicode a také aplikací ANSI.  
  
## <a name="example"></a>Příklad  
 V tématu [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)