---
title: DEFINE_COMMAND | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- DEFINE_COMMAND
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND macro
ms.assetid: 9d724968-e242-413c-9a13-e7175fccf9b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51f975b0477d29fbb35880c796f52612456c32c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101468"
---
# <a name="definecommand"></a>DEFINE_COMMAND
Určuje příkaz, který se použije k vytvoření dané sadě řádků při použití [CCommand](../../data/oledb/ccommand-class.md) třídy. Je možné zadat pouze typy řetězec odpovídající typu zadané aplikace (ANSI nebo Unicode).  
  
> [!NOTE]
>  Je doporučeno používat [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) místo `DEFINE_COMMAND`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
DEFINE_COMMAND(x, szCommand)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *x*  
 [v] Název třída uživatelského záznamu (příkaz).  
  
 `szCommand`  
 [v] Příkaz řetězec, který se použije k vytvoření dané sadě řádků při použití [CCommand](../../data/oledb/ccommand-class.md).  
  
## <a name="remarks"></a>Poznámky  
 Příkaz řetězec, který zadáte se použije jako výchozí, pokud nezadáte žádný text příkazu v [CCommand::Open](../../data/oledb/ccommand-open.md) metoda.  
  
 Tato – makro přijímá řetězců v kódu ANSI Pokud vytvoříte aplikaci jako ANSI nebo řetězců v kódu Unicode-li sestavit aplikaci ve formátu Unicode. Je doporučeno používat [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) místo `DEFINE_COMMAND`, protože bývalé přijímá řetězců v kódu Unicode, bez ohledu na typ aplikace ANSI nebo Unicode.  
  
## <a name="example"></a>Příklad  
 V tématu [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)