---
title: Podpora transakcí v prostředí OLE DB
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
ms.openlocfilehash: e7ec4f69b4bba497446c94afb94cb5a1d648f7c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209538"
---
# <a name="supporting-transactions-in-ole-db"></a>Podpora transakcí v prostředí OLE DB

[Transakce](../../data/transactions-mfc-data-access.md) je způsob, jak seskupit nebo dávkovat série aktualizací do zdroje dat tak, aby všechny úspěšné a byly potvrzeny najednou, nebo (Pokud jedna z nich selže) žádná je potvrzena a celá transakce je vrácena zpět. Tento proces zajišťuje integritu výsledku ve zdroji dat.

OLE DB podporuje transakce pomocí následujících tří metod:

- [ITransactionLocal::StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85))

- [ITransaction:: Commit](/previous-versions/windows/desktop/ms713008(v=vs.85))

- [ITransaction:: Abort](/previous-versions/windows/desktop/ms709833(v=vs.85))

## <a name="relationship-of-sessions-and-transactions"></a>Vztah relací a transakcí

Jeden objekt zdroje dat může vytvořit jeden nebo více objektů relace, z nichž každý může být uvnitř nebo vně oboru transakce v daném okamžiku.

Když relace nevstoupí do transakce, všechny činnosti provedené v této relaci v úložišti dat se okamžitě potvrdí při každém volání metody. (Někdy se označuje jako režim automatických potvrzení nebo implicitní režim.)

Když relace vstoupí do transakce, veškerá práce v rámci této relace v úložišti dat je součástí této transakce a je potvrzena nebo přerušena jako jedna jednotka. (Někdy se označuje jako režim ručního potvrzování.)

Podpora transakcí je specifická pro konkrétního poskytovatele. Pokud zprostředkovatel, který používáte, podporuje transakce, objekt relace, který podporuje `ITransaction` a `ITransactionLocal`, může zadat transakci (která není vnořená). OLE DB třídy šablon [CSession](../../data/oledb/csession-class.md) podporuje tato rozhraní a je doporučeným způsobem implementace podpory transakcí v jazyce Visual C++.

## <a name="starting-and-ending-the-transaction"></a>Zahájení a ukončení transakce

Zavoláte metody `StartTransaction`, `Commit`a `Abort` v objektu sady řádků v příjemci.

Volání `ITransactionLocal::StartTransaction` spustí novou místní transakci. Při spuštění transakce se všechny změny, které jsou vynucovány později, nepoužijí na úložiště dat, dokud transakci neodešlete.

Volání `ITransaction::Commit` nebo `ITransaction::Abort` ukončí transakci. `Commit` způsobí, že všechny změny v oboru transakce budou aplikovány na úložiště dat. `Abort` způsobí zrušení všech změn v rámci rozsahu transakce a úložiště dat zůstane ve stavu, ve kterém byl před zahájením transakce.

## <a name="nested-transactions"></a>Vnořené transakce

[Vnořená transakce](/previous-versions/windows/desktop/ms716985(v=vs.85)) probíhá při spuštění nové místní transakce, když aktivní transakce v relaci již existuje. Nová transakce je spuštěna jako vnořená transakce pod aktuální transakcí. Pokud zprostředkovatel nepodporuje vnořené transakce, volání `StartTransaction`, pokud je již aktivní transakce v relaci vrácena XACT_E_XTIONEXISTS.

## <a name="distributed-transactions"></a>Distribuované transakce

Distribuovaná transakce je transakce, která aktualizuje distribuovaná data; To znamená, že data ve více než jednom počítačovém systému v síti. Pokud chcete podporovat transakce v distribuovaném systému, měli byste místo podpory OLE DB transakcí použít .NET Framework.

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)
