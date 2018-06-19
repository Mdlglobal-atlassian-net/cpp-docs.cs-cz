---
title: Sdružování prostředků v aplikaci OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ece7ce128251f66360566c9b1965466352c4e493
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33107484"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>Sdružování prostředků v aplikaci OLE DB
Využít sdružování v aplikaci, je nutné nejprve získat zdroj dat prostřednictvím služby rozhraní OLE DB jsou vyvolány **IDataInitialize** nebo **IDBPromptInitialize**. Pokud používáte přímo `CoCreateInstance` k vyvolání zprostředkovatele podle CLSID zprostředkovatele, jsou vyvolány žádné služby rozhraní OLE DB.  
  
 Služby rozhraní OLE DB Udržovat fondy připojených zdrojů dat stejně dlouho jako odkaz na **IDataInitialize** nebo **IDBPromptInitialize** udržovaných nebo, pokud je připojení používá. Fondy jsou taky automaticky udržovat v prostředí služby COM + 1.0 nebo internetové informační služby (IIS). Pokud vaše aplikace využívá sdružování mimo prostředí služby COM + 1.0 nebo služby IIS, byste měli mít odkaz na **IDataInitialize** nebo **IDBPromptInitialize** nebo uložení do alespoň jeden připojení. Pokud chcete mít jistotu, že fondu získat zničen není, po vydání poslední připojení aplikací, zachovat odkaz, nebo počkejte na připojení po dobu jeho existence vaší aplikace.  
  
 Služby rozhraní OLE DB identifikaci fondu, ze kterého je vykreslován připojení v době, `Initialize` je volána. Po připojení vykreslením z fondu, nelze jej přesunout na jiný fond. Proto vyhnout plnění úkolů v aplikaci, které mění inicializace informace, například volání `UnInitialize` nebo volání `QueryInterface` pro specifický pro zprostředkovatele rozhraní před voláním `Initialize`. Navíc připojení s hodnotou vyzvat jiné než **DBPROMPT_NOPROMPT** nejsou ve fondu. Však inicializačního řetězce načítají připojení bylo vytvořeno prostřednictvím výzvy slouží k vytvoření další ve fondu připojení ke zdroji dat stejné.  
  
 Někteří poskytovatelé třeba samostatné připojení pro každou relaci. Tyto další připojení musí samostatně zařazena v distribuované transakce, pokud existuje. Služby rozhraní OLE DB ukládá do mezipaměti a znovu použije na jednu relaci na jeden zdroj dat, ale pokud aplikace požaduje více než jedna relace najednou z jeden zdroj dat, může zprostředkovatele skončili další připojení a provádění dalších transakce zařazení, které jsou není ve fondu. Je ve skutečnosti efektivnější vytvořit zvláštní zdroj dat pro každou relaci v prostředí ve fondu než vytvářet více relací z jednoho datového zdroje.  
  
 Nakonec protože ADO automaticky využívá technologie OLE DB služby, můžete použít ADO ke zřízení spojení a sdružování a zařazení dojít automaticky.  
  
## <a name="see-also"></a>Viz také  
 [Sdružování prostředků OLE DB a služby](../../data/oledb/ole-db-resource-pooling-and-services.md)