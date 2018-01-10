---
title: DEFINE_COMMAND_EX | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEFINE_COMMAND_EX
dev_langs: C++
helpviewer_keywords: DEFINE_COMMAND_EX macro
ms.assetid: d3e2ef20-1455-46d2-8499-8ab84bbb90a4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 851b346c8fac955f1d82c0c43fdf75c4784ca04c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="definecommandex"></a>DEFINE_COMMAND_EX
Určuje příkaz, který se použije k vytvoření dané sadě řádků při použití [CCommand](../../data/oledb/ccommand-class.md) třídy. Podporuje kódování Unicode a ANSI.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DEFINE_COMMAND_EX(  
x  
,   
wszCommand  
 )  
  
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