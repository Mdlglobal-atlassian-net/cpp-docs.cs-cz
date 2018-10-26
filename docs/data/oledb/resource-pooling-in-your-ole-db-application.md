---
title: Sdružování prostředků v aplikaci OLE DB | Dokumentace Microsoftu
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
ms.openlocfilehash: 0302f35c7de78088d1c5e662f65daf467cb1dfa2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069692"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>Sdružování prostředků v aplikaci OLE DB

Chcete-li využívají sdružování v aplikaci, je nutné jsou vyvolány získání zdroje dat pomocí služby technologie OLE DB `IDataInitialize` nebo `IDBPromptInitialize`. Pokud používáte přímo `CoCreateInstance` pro vyvolání poskytovatele podle poskytovatele CLSID, jsou vyvolány žádné služby rozhraní OLE DB.

Služby rozhraní OLE DB spravovat fondy připojených zdrojů dat. Pokud odkaz na `IDataInitialize` nebo `IDBPromptInitialize` vlastněnou nebo dokud není připojení používá. Fondy se také automaticky udržuje v rámci prostředí služby COM + 1.0 nebo internetové informační služby (IIS). Pokud vaše aplikace využívá sdružování mimo prostředí modelu COM + 1.0 služby nebo služby IIS, byste měli mít odkaz na `IDataInitialize` nebo `IDBPromptInitialize` nebo opřete se o nejméně jedno připojení. Pokud chcete mít jistotu, že fond získat není zničen, při posledním připojení vydání aplikací, zachovávat odkaz nebo blokovat připojení po dobu životnosti vaší aplikace.

Služby rozhraní OLE DB identifikaci fondu, ze které je vykreslena připojení v době, která `Initialize` je volána. Po připojení je vykreslení z fondu, nelze jej přesunout na jiný fond. Proto vyhýbání se dělání věcí ve vaší aplikaci, které se mění informace o inicializaci, jako je například volání `UnInitialize` nebo volání `QueryInterface` specifickým pro zprostředkovatele rozhraní před voláním `Initialize`. Kromě toho nejsou ve fondu připojení vytvořená pomocí výzvy jiná hodnota než DBPROMPT_NOPROMPT. Však inicializačního řetězce načte z připojení navázané prostřednictvím dotazování umožňuje vytvářet další ve fondu připojení ke stejnému zdroji dat.

Někteří poskytovatelé, třeba samostatného připojení pro každou relaci. Tyto další připojení musí samostatně zařazena v distribuované transakci, pokud existuje. Služby rozhraní OLE DB ukládá do mezipaměti a opětovně používá jedinou relaci jeden zdroj dat, ale pokud aplikace požaduje více než jedna relace současně z jednoho zdroje dat, poskytovatele může skončit další připojení a provádění dalších transakce zařazení, které jsou není ve fondu. Jde vytvořit zdroj dat pro každou relaci v prostředí ve fondu než vytvářet více relací z jednoho zdroje dat ve skutečnosti mnohem efektivnější.

A konečně protože ADO automaticky využívá technologie OLE DB služby, můžete použít ADO a navázat spojení a sdružování a zařazení probíhají automaticky.

## <a name="see-also"></a>Viz také

[Sdružování prostředků OLE DB a služby](../../data/oledb/ole-db-resource-pooling-and-services.md)