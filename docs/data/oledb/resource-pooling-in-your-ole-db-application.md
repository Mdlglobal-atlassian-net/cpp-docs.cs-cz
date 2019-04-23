---
title: Sdružování prostředků v aplikaci OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
ms.openlocfilehash: 786c2b31bb93b0691d80885c86377e2afba8c1dc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029301"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>Sdružování prostředků v aplikaci OLE DB

Chcete-li využívají sdružování v aplikaci, je nutné jsou vyvolány projít zdroje dat OLE DB služby `IDataInitialize` nebo `IDBPromptInitialize`. Pokud používáte přímo `CoCreateInstance` pro vyvolání poskytovatele podle poskytovatele CLSID, jsou vyvolány žádné služby rozhraní OLE DB.

Služby rozhraní OLE DB spravovat fondy připojených zdrojů dat. Pokud odkaz na `IDataInitialize` nebo `IDBPromptInitialize` vlastněnou nebo dokud není připojení používá. Fondy se také automaticky udržuje v rámci prostředí služby COM + 1.0 nebo internetové informační služby (IIS). Pokud vaše aplikace využívá sdružování externí služby COM + 1.0 nebo IIS prostředí, byste měli mít odkaz na `IDataInitialize` nebo `IDBPromptInitialize` nebo opřete se o nejméně jedno připojení. Pokud chcete mít jistotu, že není získat fondu zničeny při vydání poslední připojení aplikací, zachovávat odkaz nebo blokovat připojení po dobu životnosti vaší aplikace.

Služby rozhraní OLE DB identifikaci fondu, ze které je vykreslena připojení v době, která `Initialize` je volána. Po připojení je vykreslení z fondu, nelze jej přesunout na jiný fond. Ano, vyhýbání se dělání věcí ve vaší aplikaci, které se mění informace o inicializaci, jako je například volání `UnInitialize` nebo volání `QueryInterface` specifickým pro zprostředkovatele rozhraní před voláním `Initialize`. Kromě toho nejsou ve fondu připojení vytvořená pomocí výzvy jiná hodnota než DBPROMPT_NOPROMPT. Však inicializačního řetězce načte z připojení navázané prostřednictvím dotazování umožňuje vytvářet další ve fondu připojení ke stejnému zdroji dat.

Někteří poskytovatelé, třeba samostatného připojení pro každou relaci. Tyto další připojení musí samostatně zařazena v distribuované transakci, pokud existuje. OLE DB služby mezipaměti a opětovně používá jedinou relaci jeden zdroj dat, ale pokud aplikace požaduje více než jedna relace současně z jednoho zdroje dat, poskytovatele může skončit další připojení a provádění dalších transakce zařazení, které nejsou ve fondu. Je mnohem efektivnější vytvořit zdroj samostatná data pro každou relaci v prostředí než vytvářet více relací z jednoho zdroje dat ve fondu.

A konečně protože ADO automaticky využívá technologie OLE DB služby, můžete použít ADO a navázat spojení a sdružování a zařazení probíhají automaticky.

## <a name="see-also"></a>Viz také:

[Sdružování prostředků OLE DB a služby](../../data/oledb/ole-db-resource-pooling-and-services.md)