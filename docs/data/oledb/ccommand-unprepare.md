---
title: CCommand::Unprepare | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Unprepare
- CCommand.Unprepare
- CCommand::Unprepare
dev_langs: C++
helpviewer_keywords: Unprepare method
ms.assetid: 4fe59988-fe51-4c7c-a156-72b68e3d642b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ef96a0934c7ae0b336f73d20676fb9baaabbd0bf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccommandunprepare"></a>CCommand::Unprepare
Zruší aktuální plán spuštění příkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT CCommandBase::Unprepare( ) throw( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda zabalí metodu OLE DB [ICommandPrepare::Unprepare](https://msdn.microsoft.com/en-us/library/ms719635.aspx).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CCommand – třída](../../data/oledb/ccommand-class.md)