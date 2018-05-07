---
title: CCommand::Close | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CCommand.Close
- CCommand::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 4da9c02c-7082-4e47-a0fa-78b546f0f7d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5723c358e0af7cf9b92952bfd843ba90577333e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ccommandclose"></a>CCommand::Close
Uvolní přistupujícího objektu sady řádků, přidružený k příkazu.  
  
## <a name="syntax"></a>Syntaxe

```cpp
void Close();  
```  
  
## <a name="remarks"></a>Poznámky  
 Příkaz používá sadu řádků, výsledek přistupující objekt set a (volitelně) parametr přístupového objektu (na rozdíl od tabulek, které nepodporují parametry a není nutné přistupujícího objektu parametr).  
  
 Při spuštění příkazu by měly volat obě `Close` a [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) po příkazu.  
  
 Pokud chcete opakovaně stejné příkazy, má verzi přistupující objekt set každý výsledek voláním `Close` před voláním `Execute`. Na konci řady, by měl verze přistupujícího objektu parametru voláním `ReleaseCommand`. Další z typických možností je volání uložené procedury, která má výstupní parametry. Na mnoho poskytovatelů (např. zprostředkovatele OLE DB pro SQL Server) nebude možné hodnoty parametru výstup přístupný, dokud nezavřete přistupující objekt set výsledek. Volání `Close` zavřít vrácených řádků a přistupující objekt set výsledek, ale není parametr přistupujícího objektu, což umožňuje vám umožňuje načíst hodnoty parametrů výstup.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak můžete volat `Close` a `ReleaseCommand` při spuštění stejného příkazu opakovaně.  
  
 [!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CCommand – třída](../../data/oledb/ccommand-class.md)   
 [CCommand::ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)